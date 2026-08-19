---
name: Register a branded phone number with carriers
description: Register an outbound number for branded caller ID and spam remediation against a Regal business profile, track per-carrier status, update it, and remove it.
api: openapi/regal-ai-branded-phone-numbers-api-openapi.yml
operations:
  - listBusinessProfiles
  - listBrandedPhoneNumbers
  - postBrandedPhoneNumber
  - patchBrandedPhoneNumber
  - deleteBrandedPhoneNumber
generated: '2026-08-14'
method: generated
source: >-
  openapi/regal-ai-branded-phone-numbers-api-openapi.yml,
  openapi/regal-ai-business-profiles-api-openapi.yml,
  https://developer.regal.ai/reference/post-branded-phone-number
---

# Register a branded phone number with carriers

Branded caller ID puts your brand name on the recipient's handset; spam remediation gets a
mislabelled number un-flagged. Both are carrier registrations, so the interesting state is
per-carrier and asynchronous — the API call is the easy part.

## Before you call

- Base URL `https://api.regal.ai/v1`. API key raw in the `Authorization` header.
- 10 requests/second per tenant on these endpoints; 429 on exhaustion with no
  `Retry-After`.

## Steps

1. **Find the business profile.** Call `listBusinessProfiles` (`GET /businessProfiles`) and
   pick the profile whose `status` is approved. Registration binds a number to a
   `businessProfileId` (a UUID) — a profile still `in review` will fail validation with a
   400 saying the business profile was not found for this brand.

2. **Check what is already registered.** Call `listBrandedPhoneNumbers`
   (`GET /brandedPhoneNumbers`). It is cursor-paginated (`nextCursor`, `size`) and filterable
   by `phoneNumber`, `businessProfileId`, `carrier`, `feature`, `status`, `detailedStatus`,
   `internalName` and `reportingGroup`. Filter by `phoneNumber` first — this is how you avoid
   the 409 in the next step.

3. **Register with `postBrandedPhoneNumber`** (`POST /brandedPhoneNumbers`). Supply the
   `phoneNumber`, the `businessProfileId`, the branding names, and the `carrierFeatures`
   describing which feature (`brandedCallerId` or `spamRemediation`) you want on which
   carrier. Expect `201`.

   **`POST` is first-time registration only.** If the number already exists for the brand
   you get `409 Conflict` with `"Phone number +1... already exists for this brand. Use PATCH
   to update."` — that message is the instruction; switch to step 4.

4. **Update with `patchBrandedPhoneNumber`** (`PATCH /brandedPhoneNumbers/{phoneNumber}`).
   Partial update. This is also how you register or unregister the number with an individual
   carrier after the initial submission.

5. **Poll the per-carrier state.** Re-read with `listBrandedPhoneNumbers`. The record's
   top-level `status` (e.g. `"submitted for review"`) is a rollup; the truth is in
   `carrierStatuses[]`, one row per `(carrier, feature)` pair with its own `detailedStatus`
   (e.g. `pending.initialOptIn`) and `createdAt`. A number can be live on one carrier and
   pending on another. There is no webhook for carrier status changes — polling is the only
   mechanism.

6. **Remove with `deleteBrandedPhoneNumber`** (`DELETE /brandedPhoneNumbers/{phoneNumber}`).
   This fails with `400` `"Phone number not in valid status for removal"` while carrier
   submissions are still active — unregister the carriers via `patchBrandedPhoneNumber`
   first, then delete.

## Error handling

| Status | Envelope | Meaning |
|---|---|---|
| 400 | `{statusCode, message[], error}` | Validation. `message` is an **array of prose strings** — there are no field pointers or error codes. |
| 403 | `{statusCode, message, error}` | `"Invalid API Key"` — Regal returns 403, not 401, for a bad key here. |
| 404 | `{statusCode, message, error}` | Number not found for this brand. |
| 409 | `{statusCode, message, error}` | Already registered — use PATCH. |
| 429 | `{statusCode, message, error}` | `"Too many requests"`. No `Retry-After`. |

**No idempotency key exists on any of these operations.** A timed-out `POST` may have
registered the number; re-read with `listBrandedPhoneNumbers` before retrying rather than
blindly re-POSTing.

## Related

- Data model: `data-model/regal-ai-data-model.yml` (BrandedPhoneNumber → CarrierStatus)
- Errors: `errors/regal-ai-problem-types.yml`
- The same three writes exist as MCP tools (`create-branded-phone-number`,
  `update-branded-phone-number`, `delete-branded-phone-number`) — see
  `mcp/regal-ai-tool-crosswalk.yml`.
