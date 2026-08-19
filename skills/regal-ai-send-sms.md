---
name: Send an SMS through Regal
description: Send an outbound SMS from a Regal-provisioned number, with or without a campaign, honouring per-phone opt-in — and understand why the send is not safely retryable.
api: openapi/regal-ai-messages-api-openapi.yml
operations:
  - listActivePhoneNumbers
  - listCampaigns
  - sendMessage
  - postCustomEvent
generated: '2026-08-14'
method: generated
source: >-
  openapi/regal-ai-messages-api-openapi.yml,
  openapi/regal-ai-phone-numbers-api-openapi.yml,
  openapi/regal-ai-campaigns-api-openapi.yml,
  https://developer.regal.ai/reference/send-message
---

# Send an SMS through Regal

## Before you call

- Base URL `https://api.regal.ai/v1`. API key raw in the `Authorization` header.
- 10 requests/second per tenant. `429` returns `{"message":"Too Many Requests"}` (gateway
  envelope) or `{"statusCode":429,...}` (application envelope) — handle both.
- Consent is not optional. A phone reaches the wire only if `smsOptIn.subscribed` is true
  on that phone, unless you deliberately override it (see step 4).

## Steps

1. **Pick the sending number.** Call `listActivePhoneNumbers`
   (`GET /activePhoneNumbers`) and choose a number belonging to your brand. Cursor
   pagination via `nextCursor` and `size`. Use `from.phoneNumber` in the send.

2. **Optionally pick a campaign.** Call `listCampaigns` (`GET /campaigns`) and select a
   campaign with `channel: "sms"` and `state: "ready"`. Passing `campaignId` on the send
   makes the campaign supply default `content`, `from` number and opt-in behaviour.
   Anything you set explicitly in the request overrides the campaign default.

3. **Make sure the recipient exists and is opted in.** If the contact may be new, ingest it
   first with `postCustomEvent` on `https://events.regalvoice.com` (see the
   *Ingest a Regal contact and event* skill) including `smsOptIn.subscribed: true` on the
   destination phone with a timestamp and consent text.

4. **Call `sendMessage`** — `POST /messages/send`:

   ```json
   {
     "to": { "phoneNumber": "+19545552399", "bypassOptIn": false },
     "from": { "phoneNumber": "+17735550477" },
     "channel": "sms",
     "content": {
       "body": "Your appointment is confirmed for Tuesday at 2pm.",
       "mediaUrls": ["https://example.com/confirm.png"]
     }
   }
   ```

   Required: `to.phoneNumber` and `channel` (only `"sms"` is accepted). `content.body` is
   required when no `campaignId` is supplied, and caps at 1,600 characters. `mediaUrls`
   accepts **at most one** image URL — multiple attachments are not supported.

   `to.bypassOptIn: true` sends even when the recipient has not opted in. Treat that flag as
   a compliance decision, not a technical one; per-identifier consent is what keeps
   journey-triggered outbound within TCPA expectations.

5. **Read the 202.** Success is `202 Accepted`, not `200`:

   ```json
   { "status": "queued", "message": "enqueued for sms-interaction-job", "idempotencyKey": "80d65f2f3832ffeed65346056bab1cd8" }
   ```

   The message is **queued**, not delivered. Terminal delivery state arrives on the
   reporting webhooks (`sms.sent`, `sms.failed`, `sms.undelivered`) — see
   `asyncapi/regal-reporting-webhooks-asyncapi.yml`.

## The retry trap

That `idempotencyKey` in the response is **server-generated**. There is no request-side
idempotency key, no `Idempotency-Key` header, and no way to replay a send against a key you
chose. A timeout on `sendMessage` therefore leaves you unable to tell whether the SMS was
enqueued. Do not auto-retry. Reconcile from the reporting webhook stream instead, or accept
the risk of a duplicate message to a customer.

## Errors

| Status | Meaning |
|---|---|
| 400 | Validation. `message` is an array of prose, e.g. `"channel must be one of the following values: 'sms'"`, `"'content' is required when 'campaignId' is not provided."` |
| 401 | `{"message":"Unauthorized"}` — missing/unparseable Authorization header. |
| 403 | `"Invalid API Key"`. |
| 429 | Rate limited. No `Retry-After`. |

## Related

- Conventions: `conventions/regal-ai-conventions.yml`
- Errors: `errors/regal-ai-problem-types.yml`
- Webhooks: `asyncapi/regal-reporting-webhooks-asyncapi.yml`
