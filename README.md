# Regal

Regal is a New York City-based AI Agent Platform purpose-built for contact center operations. Enterprises use Regal to design, test, deploy, monitor, and improve AI Phone Agents, SMS Agents, Chat Agents, and WebRTC Voice Agents for inbound and outbound customer support, sales, scheduling, collections, and lead qualification.

This repository is an API Evangelist profile of Regal — apis.yml, OpenAPI / AsyncAPI specs, capabilities, schemas, examples, vocabulary, and plans/rate-limits/FinOps artifacts.

- Website: https://www.regal.ai
- Developer portal: https://developer.regal.ai
- API reference: https://developer.regal.ai/reference/overview
- Support: https://support.regal.ai
- Pricing: https://www.regal.ai/pricing
- Login: https://app.regal.io

## APIs

| API | Surface | Spec |
|---|---|---|
| Regal Events API | `POST https://events.regalvoice.com/events` — single Custom Events ingest endpoint (create/update contact + record event). 300 RPS default. | [openapi/regal-events-api-openapi.yml](openapi/regal-events-api-openapi.yml) |
| Regal Branded Phone Numbers API | `POST/PATCH/DELETE https://api.regal.ai/v1/brandedPhoneNumbers[/{phoneNumber}]` — branded caller ID + spam remediation. 10 RPS. | [openapi/regal-branded-phone-numbers-api-openapi.yml](openapi/regal-branded-phone-numbers-api-openapi.yml) |
| Regal Management API | `GET https://api.regal.ai/v1/{businessProfiles,activePhoneNumbers,campaigns,dispositions}` — tenant configuration listings. | [openapi/regal-management-api-openapi.yml](openapi/regal-management-api-openapi.yml) |
| Regal Messages API | `POST https://api.regal.ai/v1/messages/send` — outbound SMS tied to a campaign. 10 RPS. | [openapi/regal-messages-api-openapi.yml](openapi/regal-messages-api-openapi.yml) |
| Regal Reporting Webhooks | 40+ event types delivered to a customer-hosted HTTPS endpoint. 5-second response budget, no retries. | [asyncapi/regal-reporting-webhooks-asyncapi.yml](asyncapi/regal-reporting-webhooks-asyncapi.yml) |

## Artifacts

- `apis.yml` — apis.yml 0.20 manifest indexing every API, integration, and supporting artifact.
- `openapi/` — OpenAPI 3.1 specifications for the four REST APIs.
- `asyncapi/` — AsyncAPI 3.0 specification for the Reporting Webhooks delivery surface.
- `capabilities/` — Naftiko capability YAML for each business surface (Events, Branded Phone Numbers, Management × 4, Messages, Webhook Receiver).
- `json-schema/` — JSON Schemas for `RegalContact`, `RegalEvent`, `RegalBrandedPhoneNumber`, `RegalMessage`.
- `json-structure/` — Structural descriptions of `RegalContact` and `RegalEvent`.
- `json-ld/` — JSON-LD context aligning Regal vocabulary with schema.org.
- `examples/` — Sample request/response and webhook payloads.
- `vocabulary/` — Domain vocabulary mapping operational, resource, channel, integration, and rate-limit dimensions.
- `rules/` — Spectral ruleset enforcing Regal API conventions (HTTPS hosts, Authorization API key, Title Case summaries, 429 documentation).
- `plans/` — API Commons Plans 0.1 representation of Regal's custom enterprise pricing.
- `rate-limits/` — API Commons Rate Limits 0.1 capturing the documented per-API limits.
- `finops/` — FinOps Framework-aligned billing dimensions and export surfaces.

## Key Integrations

Data: Salesforce, HubSpot, Segment, mParticle, Zendesk, Kustomer, Klaviyo, Braze, Marketo, Customer.io, Iterable, Microsoft Dynamics 365, Zoho, Hightouch, Cal.com, Calendly, Zapier, SendGrid.

Communications: Slack, Microsoft Teams, 8x8, Five9, Talkdesk.

Reporting: Snowflake Data Share, Amazon S3, Emailed Reports, Reporting Webhooks.

Embeds: Salesforce, Kustomer, Retool, Chrome Extension.

SSO / SCIM: Google, Okta, Azure, Okta SCIM.

## Authentication

All Regal APIs use an API key passed in the `Authorization` header. API keys are obtained from Regal Support (support@regal.ai). Reporting webhook deliveries can be signed via a customer-configured header / API key set in **Regal app > Settings > Integrations**.

## Compliance

SOC 2, HIPAA, GDPR, CCPA, DPA. Customer data is not used to train LLMs.

## Maintainer

Kin Lane — kin@apievangelist.com — https://apievangelist.com
