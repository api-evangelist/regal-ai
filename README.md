# Regal

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

**Areas:** Artificial Intelligence · AI Agents · Voice AI · Contact Center · Outbound Calling · Inbound Calling · Phone Agents · SMS · Chat · WebRTC · Conversation Intelligence · Journey Orchestration

## Regal on APIs.io

Everything profiled for Regal is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/regal-ai/](https://apis.io/providers/regal-ai/)** — or go straight to one of the APIs or properties below.

### APIs (10)

- [Regal Reporting Webhooks](https://apis.io/apis/regal-ai/regal-reporting-webhooks/) — Regal publishes 40+ reporting webhook event types covering agent activity, call lifecycle (placed, completed, IVR triggered, wrapup), call recording and…
- [Regal Campaigns API](https://apis.io/apis/regal-ai/regal-ai-campaigns-api/) — The Campaigns API from Regal — 1 operation(s) for campaigns.
- [Regal Dispositions API](https://apis.io/apis/regal-ai/regal-ai-dispositions-api/) — The Dispositions API from Regal — 1 operation(s) for dispositions.
- [Regal Events API](https://apis.io/apis/regal-ai/regal-ai-events-api/) — Contact creation, update, and custom event tracking
- [Regal Messages API](https://apis.io/apis/regal-ai/regal-ai-messages-api/) — The Messages API from Regal — 1 operation(s) for messages.
- [Regal Users API](https://apis.io/apis/regal-ai/regal-ai-users-api/) — List and retrieve Regal user accounts — both human agents and AI agents — with their skills, teams, custom attributes and eligible routing queues. List…
- [Regal Active Phone Numbers API](https://apis.io/apis/regal-ai/regal-ai-activephonenumbers-api/) — The ActivePhoneNumbers API from Regal — 1 operation(s) for activephonenumbers.
- [Regal Branded Phone Numbers API](https://apis.io/apis/regal-ai/regal-ai-brandedphonenumbers-api/) — The BrandedPhoneNumbers API from Regal — 2 operation(s) for brandedphonenumbers.
- [Regal Business Profiles API](https://apis.io/apis/regal-ai/regal-ai-businessprofiles-api/) — The BusinessProfiles API from Regal — 1 operation(s) for businessprofiles.
- [Regal Call Handoffs API](https://apis.io/apis/regal-ai/regal-ai-callhandoffs-api/) — The CallHandoffs API from Regal — 1 operation(s) for callhandoffs.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Regal Reporting Webhooks](https://apis.io/asyncapis/regal-ai/regal-reporting-webhooks-asyncapi/)

#### Event channels (40)

Individual events and webhooks the provider emits.

- [/](https://apis.io/channels/regal-ai/agent-activity-updated/)
- [/](https://apis.io/channels/regal-ai/call-analysis-available/)
- [/](https://apis.io/channels/regal-ai/call-completed/)
- [/](https://apis.io/channels/regal-ai/call-ivr-triggered/)
- [/](https://apis.io/channels/regal-ai/call-placed/)
- [/](https://apis.io/channels/regal-ai/call-recording-available/)
- [/](https://apis.io/channels/regal-ai/call-transcript-available/)
- [/](https://apis.io/channels/regal-ai/call-wrapup/)
- [/](https://apis.io/channels/regal-ai/cancel-all-automated-tasks/)
- [/](https://apis.io/channels/regal-ai/contact-attribute-edited/)
- [/](https://apis.io/channels/regal-ai/contact-created/)
- [/](https://apis.io/channels/regal-ai/contact-email-created/)
- [/](https://apis.io/channels/regal-ai/contact-experiment-assigned/)
- [/](https://apis.io/channels/regal-ai/contact-phone-created/)
- [/](https://apis.io/channels/regal-ai/contact-subscribed/)
- [/](https://apis.io/channels/regal-ai/contact-unsubscribed/)
- [/](https://apis.io/channels/regal-ai/contacted-after-hours/)
- [/](https://apis.io/channels/regal-ai/custom-task-completed/)
- [/](https://apis.io/channels/regal-ai/email-conversation-completed/)
- [/](https://apis.io/channels/regal-ai/email-received/)
- [/](https://apis.io/channels/regal-ai/email-sent/)
- [/](https://apis.io/channels/regal-ai/mms-received/)
- [/](https://apis.io/channels/regal-ai/mms-sent/)
- [/](https://apis.io/channels/regal-ai/object-attribute-edited/)
- [/](https://apis.io/channels/regal-ai/object-created/)
- …and 15 more published on APIs.io

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [RegalMCP](https://apis.io/servers/regal-ai/regalmcp/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Regal Ai Agentic Access](https://apis.io/agentic-access/regal-ai/regal-ai-agentic-access/)

#### JSON Schema (4)

The data models the API reads and writes.

- [RegalBrandedPhoneNumber](https://apis.io/schemas/regal-ai/regal-branded-phone-number/)
- [RegalContact](https://apis.io/schemas/regal-ai/regal-contact/)
- [RegalEvent](https://apis.io/schemas/regal-ai/regal-event/)
- [RegalMessage](https://apis.io/schemas/regal-ai/regal-message/)

#### JSON Structure (2)

Data models expressed in JSON Structure.

- [Regal Contact Structure](https://apis.io/json-structure/regal-ai/regal-contact-structure/)
- [Regal Event Structure](https://apis.io/json-structure/regal-ai/regal-event-structure/)

#### JSON-LD (1)

Linked-data contexts for the provider's vocabulary.

- [Regal Ai Context](https://apis.io/jsonld/regal-ai/regal-ai-context/)

#### Vocabulary (1)

The provider's domain terms, defined.

- [Regal AI Vocabulary](https://apis.io/vocabularies/regal-ai/regal-ai-vocabulary/)

#### Examples (5)

Example requests and responses.

- [Regal Call Completed Webhook Example](https://apis.io/examples/regal-ai/regal-call-completed-webhook-example/)
- [Regal List Campaigns Example](https://apis.io/examples/regal-ai/regal-list-campaigns-example/)
- [Regal Post Branded Phone Number Example](https://apis.io/examples/regal-ai/regal-post-branded-phone-number-example/)
- [Regal Post Custom Event Example](https://apis.io/examples/regal-ai/regal-post-custom-event-example/)
- [Regal Send Message Example](https://apis.io/examples/regal-ai/regal-send-message-example/)

#### Collections (18)

Postman and Open Collection request collections.

- [Regal Branded Phone Numbers API](https://apis.io/collections/regal-ai/open-regal-ai-branded-phone-numbers-api/)
- [Regal Branded Phone Numbers Business Profiles API](https://apis.io/collections/regal-ai/open-regal-ai-business-profiles-api/)
- [Regal Branded Phone Numbers Campaigns API](https://apis.io/collections/regal-ai/open-regal-ai-campaigns-api/)
- [Regal Branded Phone Numbers Dispositions API](https://apis.io/collections/regal-ai/open-regal-ai-dispositions-api/)
- [Regal Branded Phone Numbers Events API](https://apis.io/collections/regal-ai/open-regal-ai-events-api/)
- [Regal Branded Phone Numbers Messages API](https://apis.io/collections/regal-ai/open-regal-ai-messages-api/)
- [Regal Branded Phone Numbers API](https://apis.io/collections/regal-ai/open-regal-ai-phone-numbers-api/)
- [Regal Branded Phone Numbers API](https://apis.io/collections/regal-ai/open-regal-branded-phone-numbers-api/)
- [Regal Events API](https://apis.io/collections/regal-ai/open-regal-events-api/)
- [Regal Management API](https://apis.io/collections/regal-ai/open-regal-management-api/)
- [Regal Messages API](https://apis.io/collections/regal-ai/open-regal-messages-api/)
- [Regal Branded Phone Numbers API](https://apis.io/collections/regal-ai/postman-regal-ai-branded-phone-numbers-api/)
- [Regal Branded Phone Numbers Business Profiles API](https://apis.io/collections/regal-ai/postman-regal-ai-business-profiles-api/)
- [Regal Branded Phone Numbers Campaigns API](https://apis.io/collections/regal-ai/postman-regal-ai-campaigns-api/)
- [Regal Branded Phone Numbers Dispositions API](https://apis.io/collections/regal-ai/postman-regal-ai-dispositions-api/)
- [Regal Branded Phone Numbers Events API](https://apis.io/collections/regal-ai/postman-regal-ai-events-api/)
- [Regal Branded Phone Numbers Messages API](https://apis.io/collections/regal-ai/postman-regal-ai-messages-api/)
- [Regal Branded Phone Numbers API](https://apis.io/collections/regal-ai/postman-regal-ai-phone-numbers-api/)

#### Overlays (18)

OpenAPI overlays, including conversational phrasing for each operation.

- [Regal Ai Activephonenumbers Api Phrasing Overlay](https://apis.io/overlays/regal-ai/regal-ai-activephonenumbers-api-phrasing-overlay/)
- [Regal Ai Branded Phone Numbers Overlay](https://apis.io/overlays/regal-ai/regal-ai-branded-phone-numbers-overlay/)
- [Regal Ai Brandedphonenumbers Api Phrasing Overlay](https://apis.io/overlays/regal-ai/regal-ai-brandedphonenumbers-api-phrasing-overlay/)
- [Regal Ai Business Profiles Overlay](https://apis.io/overlays/regal-ai/regal-ai-business-profiles-overlay/)
- [Regal Ai Businessprofiles Api Phrasing Overlay](https://apis.io/overlays/regal-ai/regal-ai-businessprofiles-api-phrasing-overlay/)
- [Regal Ai Call Handoffs Overlay](https://apis.io/overlays/regal-ai/regal-ai-call-handoffs-overlay/)
- [Regal Ai Callhandoffs Api Phrasing Overlay](https://apis.io/overlays/regal-ai/regal-ai-callhandoffs-api-phrasing-overlay/)
- [Regal Ai Campaigns Api Phrasing Overlay](https://apis.io/overlays/regal-ai/regal-ai-campaigns-api-phrasing-overlay/)
- [Regal Ai Campaigns Overlay](https://apis.io/overlays/regal-ai/regal-ai-campaigns-overlay/)
- [Regal Ai Dispositions Api Phrasing Overlay](https://apis.io/overlays/regal-ai/regal-ai-dispositions-api-phrasing-overlay/)
- [Regal Ai Dispositions Overlay](https://apis.io/overlays/regal-ai/regal-ai-dispositions-overlay/)
- [Regal Ai Events Api Phrasing Overlay](https://apis.io/overlays/regal-ai/regal-ai-events-api-phrasing-overlay/)
- [Regal Ai Events Overlay](https://apis.io/overlays/regal-ai/regal-ai-events-overlay/)
- [Regal Ai Messages Api Phrasing Overlay](https://apis.io/overlays/regal-ai/regal-ai-messages-api-phrasing-overlay/)
- [Regal Ai Messages Overlay](https://apis.io/overlays/regal-ai/regal-ai-messages-overlay/)
- [Regal Ai Phone Numbers Overlay](https://apis.io/overlays/regal-ai/regal-ai-phone-numbers-overlay/)
- [Regal Ai Users Api Phrasing Overlay](https://apis.io/overlays/regal-ai/regal-ai-users-api-phrasing-overlay/)
- [Regal Ai Users Overlay](https://apis.io/overlays/regal-ai/regal-ai-users-overlay/)

#### Governance rules (3)

Spectral rulesets for the provider's contracts.

- [Regal — asyncapi rules](https://apis.io/rules/regal-ai/regal-ai-asyncapi-spectral-rules/)
- [Regal — jsonschema rules](https://apis.io/rules/regal-ai/regal-ai-jsonschema-spectral-rules/)
- [Regal — regal rules](https://apis.io/rules/regal-ai/regal-rules/)

#### Security (4)

Authentication, trust centre, and vulnerability disclosure.

- [Regal Ai Authentication](https://apis.io/security/regal-ai/regal-ai-authentication/)
- [Regal Ai Domain Security](https://apis.io/security/regal-ai/regal-ai-domain-security/)
- [Regal Ai Trust Center](https://apis.io/security/regal-ai/regal-ai-trust-center/)
- [Regal Ai Vulnerability Disclosure](https://apis.io/security/regal-ai/regal-ai-vulnerability-disclosure/)

#### OAuth scopes (1)

The permissions the API asks for.

- [Regal Ai Scopes](https://apis.io/scopes/regal-ai/regal-ai-scopes/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Regal Ai Plans Pricing](https://apis.io/plans/regal-ai/regal-ai-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Regal Ai Rate Limits](https://apis.io/rate-limits/regal-ai/regal-ai-rate-limits/)

#### FinOps (1)

What the API costs to run, by operation.

- [Regal Ai Finops](https://apis.io/finops/regal-ai/regal-ai-finops/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.regal.ai/)
- [Documentation](https://developer.regal.ai)
- [Getting started](https://developer.regal.ai/docs/plan-your-implementation)
- [API reference](https://developer.regal.ai/reference/api)
- [Pricing](https://www.regal.ai/pricing)
- [Sign up](https://www.regal.ai/get-a-demo)
- [Support](https://support.regal.ai/hc/en-us)
- [Changelog](https://www.regal.ai/blog/january-2025-releases)
- [Blog](https://www.regal.ai/blog)
- [Security](https://www.regal.ai/security)
- [Compliance](https://www.regal.ai/security)
- [Trust centre](https://www.regal.ai/security)
- [Terms of service](https://www.regal.ai/terms-of-service)
- [Privacy policy](https://www.regal.ai/privacy-policy)
- [GitHub](https://github.com/regal-ai)
- [Status](https://status.regal.ai)

## API Evangelist rating

**Kin Score 70.0** — exemplar · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 71.7 |
| Contract quality | 72.8 |
| Contract governance | 45.5 |
| Operational transparency | 84.2 |
| Developer ergonomics | 63.7 |
| Access clarity | 64.5 |

**Agent readiness 54.9** — agent-ready (gated down from agent-native)

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | verified |
| Auth Clarity | served (partial credit) |
| Idempotency | — |
| Error Semantics | derived (partial credit) |
| OpenAPI Examples | verified |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | derived (partial credit) |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | served (partial credit) |
| Protected Resource Metadata | verified |
| Dynamic Client Registration | yes |
| Agentic Commerce | — |
| Pagination Ratio | paginated |
| Operation Distinctiveness | distinct |

**Regulatory alignment 42.2** — Telecommunications

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/regal-ai/](https://apis.io/providers/regal-ai/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Regal: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/regal-ai/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
