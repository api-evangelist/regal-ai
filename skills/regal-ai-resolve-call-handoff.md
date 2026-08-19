---
name: Resolve a Regal AI call handoff
description: After a Regal AI voice agent leaves a live call, retrieve the routing decision and call context by callKey and resolve the destination against Regal users and dispositions.
api: openapi/regal-ai-call-handoffs-api-openapi.yml
operations:
  - getCallHandoff
  - listUsers
  - getUser
  - listDispositions
generated: '2026-08-14'
method: generated
source: >-
  openapi/regal-ai-call-handoffs-api-openapi.yml,
  openapi/regal-ai-users-api-openapi.yml,
  openapi/regal-ai-dispositions-api-openapi.yml,
  https://developer.regal.ai/reference/call-handoff
---

# Resolve a Regal AI call handoff

When a Regal AI voice agent finishes with a live call it records where the call should go
next and what it learned. This skill retrieves that decision so a downstream contact-centre
platform can act on it.

**Scope**: Regal documents this endpoint as currently enabled only for inbound calls
connected through the **Five9 AI Agent Connect** integration. Several response fields are
marked "Five 9 Exclusive". Do not build against it for other telephony paths.

## Before you call

- Base URL `https://api.regal.ai/v1`. API key raw in the `Authorization` header.
- 10 requests/second. `429 Rate Limit Exceeded` on exhaustion, with no `Retry-After`.
- You need the `callKey` from the telephony side. There is no list endpoint — this is a
  point lookup only.

## Steps

1. **Call `getCallHandoff`** — `GET /callHandoffs/{callKey}`. The optional `provider` query
   parameter identifies the telephony provider.

2. **Branch on `route.type`.** It is one of:

   | `route.type` | `route.value` holds |
   |---|---|
   | `skill` | the Five9 skill name (a queue) |
   | `external` | a phone number |
   | `agent` | a Five9 agent username |
   | `hangup` | `agent_hangup`, `user_hangup`, or `error` |

   `route.reason` carries your configured Transfer Destination reason on transfers, or a
   descriptor of what happened on hangups.

3. **Read the context bags.** Three families of dynamic keys ride along:
   - `meta.*` — static metadata from the integration configuration and, on a cold transfer,
     the transfer-destination configuration (e.g. `meta.priority: "high"`).
   - `task.*` — the related task attributes plus the task SID (e.g. `task.sid: "WT123"`,
     `task.direction: "inbound"`, `task.incomingSipHeaders.X-CallSessionId`).
   - `definedContactData.*` — values the agent collected in-conversation via **Set Contact
     Data** actions in the Agent Builder (e.g. `definedContactData.firstName: "Jane"`).

   These are open key spaces: do not hard-code a schema, iterate the prefixes.

4. **Resolve a human destination.** When `route.type` is `agent`, resolve the username
   against Regal with `getUser` (`GET /users/{userIdOrEmail}` — accepts a Regal user UUID or
   an exact, URL-encoded login email) to get their skills, teams, custom attributes and
   eligible queues. To search rather than look up, use `listUsers` (`GET /users`) with
   `email`, `skills`, `teams`, `queues` or `customAttributes` filters plus `nextCursor`/`size`.
   Note that Regal "users" include both human and AI agents.

5. **Reconcile the outcome.** Pull the account's disposition vocabulary once with
   `listDispositions` (`GET /dispositions`) and cache it — each entry carries `disposition`,
   `description`, `isSystem` and `conversationHappened` — then map the call's disposition
   from the reporting webhook stream against it.

## Errors

| Status | Meaning |
|---|---|
| 400 | Bad Request — malformed `callKey` or `provider`. |
| 401 | Unauthorized — missing or unparseable Authorization header. |
| 403 | Forbidden — key not valid for this brand. |
| 404 | `"No handoff data found for the given callKey"` — either the key is wrong or the handoff has not been written yet. Treat 404 as "not ready", back off, retry once; it is not necessarily permanent. |

There is no `Retry-After` and no 5xx documented on this operation.

## Related

- Data model: `data-model/regal-ai-data-model.yml` (CallHandoff → Task → Queue)
- Webhooks (where the call lifecycle actually streams): `asyncapi/regal-reporting-webhooks-asyncapi.yml`
- Errors: `errors/regal-ai-problem-types.yml`
