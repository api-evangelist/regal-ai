---
name: Ingest a Regal contact and event
description: Create or update a Regal contact profile and record a custom event on it through the Custom Events ingest endpoint, with correct identity resolution and per-identifier consent.
api: openapi/regal-ai-events-api-openapi.yml
operations:
  - postCustomEvent
generated: '2026-08-14'
method: generated
source: openapi/regal-ai-events-api-openapi.yml + https://developer.regal.ai/reference/overview
---

# Ingest a Regal contact and event

This is the only public write path into Regal's customer data. One endpoint creates a
contact, updates a contact, and records an event — the payload decides which.

## Before you call

- **Base URL is not the management host.** This endpoint lives on
  `https://events.regalvoice.com`, *not* `https://api.regal.ai/v1`.
- **Auth**: put the API key raw in the `Authorization` header. No `Bearer` prefix. Keys are
  issued by Regal support (support@regal.ai); there is no self-serve key page and no
  test/live key pair — you are always writing to production data.
- **Rate limit**: 300 requests/second per tenant. A 429 carries no `Retry-After` and no
  `RateLimit-*` headers, so pace client-side.

## Steps

1. **Decide what makes this contact contactable.** A contact exists in Regal only if it has
   at least one phone or email. If you have neither, `postCustomEvent` will not create a
   profile and the event cannot trigger a journey.

2. **Send the identifiers in the payload.** Regal resolves identity in the order
   **phone number → email address → userId**, attaching to the first match and creating a
   new profile if none match. Include `userId` (your own database id) on every call you
   can — it is the only identifier that is stable across your systems.

3. **Call `postCustomEvent`** — `POST /events` on `https://events.regalvoice.com`:

   ```json
   {
     "userId": "123",
     "traits": {
       "firstName": "Rebecca",
       "lastName": "Greene",
       "phones": {
         "+19545552399": {
           "label": "Mobile",
           "isPrimary": true,
           "voiceOptIn": { "subscribed": true, "timestamp": "2026-08-14T09:12:28-04:00", "text": "I agree to receive marketing calls" },
           "smsOptIn": { "subscribed": true }
         }
       },
       "emails": {
         "rebecca@example.com": { "isPrimary": true, "emailOptIn": { "subscribed": true } }
       }
     },
     "name": "Application Completed",
     "properties": { "program": "Phlebotomy Course", "course_type": "In Person" },
     "originalTimestamp": "2026-08-14T09:12:28-04:00",
     "eventSource": "crm"
   }
   ```

   Traits and event data may travel in the **same** call — you do not need two requests to
   update the profile and record the event.

4. **Carry consent per identifier, not per contact.** `voiceOptIn` / `smsOptIn` hang off
   each phone; `emailOptIn` hangs off each email. Only `subscribed` is required; add
   `timestamp`, `ip` and `text` for the audit trail. Journey-triggered calls and SMS reach
   the **primary** phone only — if you promote a new primary phone without carrying its
   opt-in, outbound contact silently stops.

5. **Handle the response.** `200` on success. `400` and `401` use the gateway envelope
   `{"message": "..."}`.

## Rules that will bite you

- **Data types are cast on first write and are permanent.** A trait or event property that
  first arrives as a string stays a string. Later values that cannot be coerced do not fail
  the API call — they fail later, inside journey conditional nodes. Normalise types at the
  source.
- **There is a hard ceiling of 8,000 unique event property names per account**, counted per
  event-name/property-name pair. Prefer one event name with categorising properties over
  many near-identical event names.
- **No idempotency.** There is no `Idempotency-Key` header and no request-side idempotency
  field. A retried `postCustomEvent` appends a duplicate *event* (identity resolution
  dedupes the profile, not the event). Retry only when a duplicate event is acceptable.
- **You cannot read back.** There is no public REST endpoint that returns a contact profile.
  To verify, use the Regal MCP server (`lookup-profile`, `fetch-profile`,
  `fetch-profile-events`) or the Recent Activity / Audience pages in the app.

## Related

- Conventions: `conventions/regal-ai-conventions.yml`
- Errors: `errors/regal-ai-problem-types.yml`
- Rate limits: `rate-limits/regal-ai-rate-limits.yml`
