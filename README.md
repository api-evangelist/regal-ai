# Regal (regal-ai)

Regal is a New York City-based AI Agent Platform purpose-built for contact center operations. The Regal platform lets enterprises design, test, deploy, monitor, and continuously improve AI Phone Agents, SMS Agents, Chat Agents, and WebRTC Voice Agents for inbound and outbound use cases including sales, customer support, scheduling, collections, and lead qualification. The product surface includes an Agent Builder (no-code prompts, actions, knowledge base, variants, languages, LLM models), a Sales Dialer, Journey Builder for orchestrating multi-channel customer experiences, Conversation Intelligence for QA and analytics, and a Copilot that automates agent design. Regal exposes a public REST API spanning a Custom Events ingest endpoint (events.regalvoice.com/events) for contact and event ingestion plus a v1 management API (api.regal.ai/v1) covering Branded Phone Numbers, Business Profiles, Active Phone Numbers, Campaigns, Dispositions, and outbound SMS message sending. The platform also publishes 40+ reporting webhook event types covering calls, SMS, MMS, email, voicemail, agent activity, contacts, and journey state, plus a Custom Actions framework that lets voice agents call out to customer-owned HTTP endpoints during conversations. Regal integrates natively with Segment, mParticle, HubSpot, Salesforce, Zendesk, Kustomer, Klaviyo, Braze, Marketo, Customer.io, Iterable, Microsoft Dynamics 365, Zoho, Hightouch, Cal.com, Calendly, Snowflake, S3, Slack, Microsoft Teams, Five9, Talkdesk, and 8x8.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/regal-ai/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/regal-ai/refs/heads/main/apis.yml)

## Scope

- **Position:** Consuming
- **Access:** 3rd-Party

## Tags

- AI
- AI Agents
- Voice AI
- Contact Center
- Outbound Calling
- Inbound Calling
- Phone Agents
- SMS
- Chat
- WebRTC
- Conversation Intelligence
- Journey Orchestration
- Branded Caller ID
- CCaaS
- CPaaS
- Sales Dialer
- Customer Engagement

## Timestamps

- **Created:** 2026-05-24
- **Modified:** 2026-05-24

## APIs

### Regal Events API

The Regal Events API is a single high-throughput ingest endpoint (POST https://events.regalvoice.com/events) that creates or updates a contact and records a custom event on the contact profile. The body uses a userId plus a traits object (phones, emails, firstName, lastName, address, custom properties) and a top-level name/properties pair describing the event. Identity resolution iterates identifiers in the order primary phone > any other phone > primary email > any other email > userId. A contact must have at least one phone or email to be considered contactable. Authenticated via API key in the Authorization header. Rate limited to 300 requests per second by default. This is the same endpoint that triggers Journeys (and therefore outbound calls, SMS journeys, and reminder sequences) when paired with the correct event name and TCPA opt-in flags.

- **Human URL:** [https://developer.regal.ai/reference/api](https://developer.regal.ai/reference/api)

#### Tags

- Events
- Contacts
- Identity Resolution
- Ingestion
- Custom Events

#### Properties

- [Documentation](https://developer.regal.ai/reference/overview)
- [Documentation](https://developer.regal.ai/reference/api)
- [Documentation](https://developer.regal.ai/docs/send-custom-event-to-regal)
- [F A Q](https://developer.regal.ai/reference/faq)
- [OpenAPI](openapi/regal-events-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/regal-events-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/regal-events-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [JSON Schema](json-schema/regal-contact-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/regal-event-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON-LD](json-ld/regal-ai-context.jsonld) — [JSON-LD](https://www.w3.org/TR/json-ld11/)

### Regal Branded Phone Numbers API

The Branded Phone Numbers API at api.regal.ai/v1/brandedPhoneNumbers lets you register, update, and remove branded caller ID and spam remediation entries on a per-carrier, per-feature basis. POST creates a new registration tying a phoneNumber to a businessProfileId and a carrierFeatures array (with brandingNameShort, brandingNameLong, internalName, reportingGroup, and one of spamRemediation or brandedCallerId enabled). PATCH updates the registration partially. DELETE removes it once all carrier submissions are inactive. The surface is rate limited to 10 requests per second.

- **Human URL:** [https://developer.regal.ai/reference/post-branded-phone-number](https://developer.regal.ai/reference/post-branded-phone-number)

#### Tags

- Branded Caller ID
- Phone Numbers
- Trust Center
- Carrier Registration

#### Properties

- [Documentation](https://developer.regal.ai/reference/post-branded-phone-number)
- [Documentation](https://developer.regal.ai/reference/patch-branded-phone-number)
- [Documentation](https://developer.regal.ai/reference/delete-branded-phone-number)
- [OpenAPI](openapi/regal-branded-phone-numbers-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/regal-branded-phone-numbers-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/regal-branded-phone-numbers-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [JSON Schema](json-schema/regal-branded-phone-number-schema.json) — [JSON Schema](https://json-schema.org/specification)

### Regal Management API

The Management API exposes read-only listing endpoints over api.regal.ai/v1 covering Business Profiles (used to drive branded caller ID), Active Phone Numbers in your tenant, Outbound Campaigns, and AI Call Dispositions. These endpoints were introduced in the January 2025 release to enable programmatic onboarding, audit, and reporting against the tenant's configuration without screen-scraping the Regal app UI.

- **Human URL:** [https://developer.regal.ai/reference/overview](https://developer.regal.ai/reference/overview)

#### Tags

- Business Profiles
- Phone Numbers
- Campaigns
- Dispositions
- Account

#### Properties

- [Documentation](https://developer.regal.ai/reference/overview)
- [Changelog](https://www.regal.ai/blog/january-2025-releases)
- [OpenAPI](openapi/regal-management-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/regal-management-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/regal-management-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Regal Messages API

The Messages API at POST https://api.regal.ai/v1/messages/send delivers outbound SMS messages tied to a Regal SMS campaign. The body requires a to recipient object, a channel value of "sms", and either a campaignId (which supplies default from-number and content) or an explicit from object and content object. Unknown destination numbers are automatically resolved to new contact profiles. Returns 202 Accepted for queued messages and is rate limited to 10 requests per second.

- **Human URL:** [https://developer.regal.ai/reference/send-message](https://developer.regal.ai/reference/send-message)

#### Tags

- SMS
- Messaging
- Outbound
- Campaigns

#### Properties

- [Documentation](https://developer.regal.ai/reference/send-message)
- [OpenAPI](openapi/regal-messages-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/regal-messages-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/regal-messages-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [JSON Schema](json-schema/regal-message-schema.json) — [JSON Schema](https://json-schema.org/specification)

### Regal Reporting Webhooks

Regal publishes 40+ reporting webhook event types covering agent activity, call lifecycle (placed, completed, IVR triggered, wrapup), call recording and transcript availability, AI call analysis, task reservations, SMS lifecycle (queued, sent, received, failed, undelivered, conversation completed), MMS, email, voicemail (recording and transcript availability, completion), contact lifecycle (created, subscribed, unsubscribed, attribute and phone/email edits, experiment assignment), scheduled callbacks and reminders, custom tasks, custom objects, and cancel-all-automated-tasks signals. Each event carries a common envelope (userId, traits, name, eventId, properties, originalTimestamp, eventSource) plus event-specific properties. Webhooks must respond within five seconds or the event is dropped (no retries); endpoint changes take up to five minutes to propagate.

- **Human URL:** [https://developer.regal.ai/docs/reporting-webhooks](https://developer.regal.ai/docs/reporting-webhooks)

#### Tags

- Webhooks
- Events
- Reporting
- Streaming
- AsyncAPI

#### Properties

- [Documentation](https://developer.regal.ai/docs/reporting-webhooks)
- [Documentation](https://support.regal.ai/hc/en-us/articles/5725272620187-How-to-Use-Journey-Webhooks)
- [AsyncAPI](asyncapi/regal-reporting-webhooks-asyncapi.yml) — [AsyncAPI Specification](https://www.asyncapi.com/docs/reference/specification/latest)
- [Postman Collection](collections/regal-branded-phone-numbers-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/regal-branded-phone-numbers-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Postman Collection](collections/regal-events-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/regal-events-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Postman Collection](collections/regal-management-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/regal-management-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Postman Collection](collections/regal-messages-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/regal-messages-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [Portal](https://www.regal.ai)
- [Documentation](https://developer.regal.ai)
- [Documentation](https://developer.regal.ai/docs)
- [Documentation](https://developer.regal.ai/reference/overview)
- [Getting Started](https://developer.regal.ai/docs/plan-your-implementation)
- [Documentation](https://developer.regal.ai/llms.txt)
- [F A Q](https://developer.regal.ai/reference/faq)
- [Support Portal](https://support.regal.ai/hc/en-us)
- [Documentation](https://support.regal.ai/hc/en-us/articles/5725458229531-Integration-Guides-API-Docs)
- [Login](https://app.regal.io)
- [Sign Up](https://www.regal.ai/get-a-demo)
- [Pricing](https://www.regal.ai/pricing)
- [Plans](plans/regal-ai-plans-pricing.yml)
- [Rate Limits](rate-limits/regal-ai-rate-limits.yml)
- [Fin Ops](finops/regal-ai-finops.yml)
- [Blog](https://www.regal.ai/blog)
- [Changelog](https://www.regal.ai/blog/january-2025-releases)
- [Customers](https://www.regal.ai/customers)
- [Product](https://www.regal.ai/ai-agents)
- [Product](https://www.regal.ai/sales-dialer)
- [Product](https://www.regal.ai/journey-builder)
- [Product](https://www.regal.ai/conversation-intelligence)
- [Careers](https://www.regal.ai/careers)
- [Company](https://www.regal.ai/about)
- [Contact](https://www.regal.ai/contact)
- [Trust Center](https://www.regal.ai/security)
- [Privacy Policy](https://www.regal.ai/privacy-policy)
- [Terms of Service](https://www.regal.ai/terms-of-service)
- [LinkedIn](https://www.linkedin.com/company/regal-ai-official)
- [Twitter](https://twitter.com/regalio)
- [YouTube](https://www.youtube.com/@regalio)
- [Integrations](https://developer.regal.ai/docs/salesforce)
- [Integrations](https://developer.regal.ai/docs/hubspot)
- [Integrations](https://developer.regal.ai/docs/segment)
- [Integrations](https://developer.regal.ai/docs/mparticle)
- [Integrations](https://developer.regal.ai/docs/zendesk)
- [Integrations](https://developer.regal.ai/docs/kustomer)
- [Integrations](https://developer.regal.ai/docs/klaviyo)
- [Integrations](https://developer.regal.ai/docs/braze)
- [Integrations](https://developer.regal.ai/docs/marketo)
- [Integrations](https://developer.regal.ai/docs/customerio)
- [Integrations](https://developer.regal.ai/docs/iterable)
- [Integrations](https://developer.regal.ai/docs/microsoft-dynamics-365)
- [Integrations](https://developer.regal.ai/docs/zoho)
- [Integrations](https://developer.regal.ai/docs/hightouch)
- [Integrations](https://developer.regal.ai/docs/calcom)
- [Integrations](https://developer.regal.ai/docs/calendly)
- [Integrations](https://developer.regal.ai/docs/zapier)
- [Integrations](https://developer.regal.ai/docs/sendgrid)
- [Integrations](https://developer.regal.ai/docs/slack)
- [Integrations](https://developer.regal.ai/docs/microsoft-teams)
- [Integrations](https://developer.regal.ai/docs/8x8)
- [Integrations](https://developer.regal.ai/docs/five9)
- [Integrations](https://developer.regal.ai/docs/talkdesk)
- [Integrations](https://developer.regal.ai/docs/snowflake-data-share)
- [Integrations](https://developer.regal.ai/docs/amazon-s3)
- [Integrations](https://developer.regal.ai/docs/freshdesk)
- [Integrations](https://developer.regal.ai/docs/assembled)
- [Integrations](https://developer.regal.ai/docs/gong)
- [Integrations](https://developer.regal.ai/docs/balto)
- [Integrations](https://developer.regal.ai/docs/kindlyai)
- [Embed](https://developer.regal.ai/docs/salesforce-embed)
- [Embed](https://developer.regal.ai/docs/kustomer-embed)
- [Embed](https://developer.regal.ai/docs/retool)
- [Embed](https://developer.regal.ai/docs/chrome-extension)
- [Single Sign On](https://developer.regal.ai/docs/google-sso)
- [Single Sign On](https://developer.regal.ai/docs/okta-sso)
- [Single Sign On](https://developer.regal.ai/docs/azure-sso)
- [S C I M](https://developer.regal.ai/docs/okta-scim)
- [Vocabulary](vocabulary/regal-ai-vocabulary.yml)
- [Features](undefined)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
**URL:** https://apievangelist.com
