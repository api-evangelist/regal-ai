# Regal (regal-ai)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

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
