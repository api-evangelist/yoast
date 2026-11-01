# Yoast

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

Yoast is the maker of the world's most popular WordPress SEO plugin, active on over 13 million sites, and is part of Newfold Digital. Yoast provides developer APIs for integrating SEO metadata, structured data (Schema.org), meta tags, sitemaps, and SEO analysis into headless WordPress sites and third-party platforms. Most of that surface ships as plugin code and runs on the customer's own WordPress install: the Yoast REST API (/wp-json/yoast/v1/get_head plus yoast_head_json on WP posts and pages), the Schema Aggregator API that emits a site's whole Schema.org graph as JSON-L, the Surfaces, Metadata and Schema PHP APIs, and — since Yoast SEO 27.5 — three read-only WordPress Abilities that hand SEO, readability and inclusive-language scores to AI agents. Yoast additionally operates one hosted API of its own, the MyYoast Provisioning (Subscription) API at my.yoast.com, a partner-gated Basic Auth surface for resellers, backed by an OpenID Connect issuer with dynamic client registration, PKCE and DPoP. Key products include Yoast SEO Free, Yoast SEO Premium, Yoast SEO for Shopify, WooCommerce SEO, Local SEO, Video SEO, and News SEO.

**Areas:** SEO · WordPress · Content Optimization · Schema · Metadata · Structured Data · Content Analysis · Agent Readiness · Plugins

## Yoast on APIs.io

Everything profiled for Yoast is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/yoast/](https://apis.io/providers/yoast/)** — or go straight to one of the APIs or properties below.

### APIs (12)

- [Yoast Surfaces API](https://apis.io/apis/yoast/yoast-surfaces-api/) — The Yoast Surfaces API provides a PHP interface for retrieving SEO metadata programmatically within WordPress. It exposes the YoastSEO() surface with…
- [Yoast Metadata API](https://apis.io/apis/yoast/yoast-metadata-api/) — The Yoast Metadata API provides a PHP interface to add, alter, or remove metadata in the <head> of a WordPress document. Developers can hook into Yoast's…
- [Yoast Schema API](https://apis.io/apis/yoast/yoast-schema-api/) — The Yoast Schema API provides a PHP interface for customizing the Schema.org JSON-LD structured data output generated by Yoast SEO. Developers can add,…
- [Yoast Pages API](https://apis.io/apis/yoast/yoast-pages-api/) — WordPress page SEO metadata via WP REST API
- [Yoast Posts API](https://apis.io/apis/yoast/yoast-posts-api/) — WordPress post SEO metadata via WP REST API
- [Yoast SEO Head API](https://apis.io/apis/yoast/yoast-seo-head-api/) — Retrieve SEO metadata for any URL
- [Yoast SEO Abilities API](https://apis.io/apis/yoast/yoast-abilities-api/) — Yoast SEO registers its content-analysis results as WordPress Abilities (the Abilities API introduced in WordPress 6.9), making them discoverable and…
- [Yoast Provisioning Account API](https://apis.io/apis/yoast/yoast-provisioning-account-api/) — Provisioner account self-service
- [Yoast Provisioning Downloads API](https://apis.io/apis/yoast/yoast-provisioning-downloads-api/) — Current product versions and download URLs for a product code
- [Yoast Provisioning Users API](https://apis.io/apis/yoast/yoast-provisioning-users-api/) — Customer-level operations, including scheduled GDPR delete
- [Yoast Schema Aggregator API](https://apis.io/apis/yoast/yoast-schema-aggregator-api/) — Aggregated Schema.org output for a WordPress site
- [Yoast Subscription Provisioning API](https://apis.io/apis/yoast/yoast-subscription-provisioning-api/) — Create, read and manage provisioned Yoast subscriptions

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [yoast](https://apis.io/servers/yoast/yoast/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Yoast Agentic Access](https://apis.io/agentic-access/yoast/yoast-agentic-access/)

#### JSON Schema (1)

The data models the API reads and writes.

- [Yoast SEO Metadata](https://apis.io/schemas/yoast/yoast-seo-metadata/)

#### JSON Structure (1)

Data models expressed in JSON Structure.

- [Yoast Seo Metadata Structure](https://apis.io/json-structure/yoast/yoast-seo-metadata-structure/)

#### JSON-LD (1)

Linked-data contexts for the provider's vocabulary.

- [Yoast Context](https://apis.io/jsonld/yoast/yoast-context/)

#### Vocabulary (1)

The provider's domain terms, defined.

- [Yoast Vocabulary](https://apis.io/vocabularies/yoast/yoast-vocabulary/)

#### Examples (2)

Example requests and responses.

- [Yoast Rest Get Post Seo Example](https://apis.io/examples/yoast/yoast-rest-get-post-seo-example/)
- [Yoast Rest Get Seo Head Example](https://apis.io/examples/yoast/yoast-rest-get-seo-head-example/)

#### Collections (4)

Postman and Open Collection request collections.

- [Yoast REST Pages API](https://apis.io/collections/yoast/open-yoast-pages-api/)
- [Yoast REST Pages Posts API](https://apis.io/collections/yoast/open-yoast-posts-api/)
- [Yoast REST API](https://apis.io/collections/yoast/open-yoast-rest/)
- [Yoast REST Pages SEO Head API](https://apis.io/collections/yoast/open-yoast-seo-head-api/)

#### Overlays (6)

OpenAPI overlays, including conversational phrasing for each operation.

- [Yoast Abilities Overlay](https://apis.io/overlays/yoast/yoast-abilities-overlay/)
- [Yoast Myyoast Provisioning Overlay](https://apis.io/overlays/yoast/yoast-myyoast-provisioning-overlay/)
- [Yoast Pages Overlay](https://apis.io/overlays/yoast/yoast-pages-overlay/)
- [Yoast Posts Overlay](https://apis.io/overlays/yoast/yoast-posts-overlay/)
- [Yoast Schema Aggregator Overlay](https://apis.io/overlays/yoast/yoast-schema-aggregator-overlay/)
- [Yoast Seo Head Overlay](https://apis.io/overlays/yoast/yoast-seo-head-overlay/)

#### Governance rules (2)

Spectral rulesets for the provider's contracts.

- [Yoast — jsonschema rules](https://apis.io/rules/yoast/yoast-jsonschema-spectral-rules/)
- [Yoast API Rules](https://apis.io/rules/yoast/yoast-rules/)

#### Security (3)

Authentication, trust centre, and vulnerability disclosure.

- [Yoast Authentication](https://apis.io/security/yoast/yoast-authentication/)
- [Yoast Domain Security](https://apis.io/security/yoast/yoast-domain-security/)
- [Yoast Vulnerability Disclosure](https://apis.io/security/yoast/yoast-vulnerability-disclosure/)

#### OAuth scopes (1)

The permissions the API asks for.

- [Yoast Scopes](https://apis.io/scopes/yoast/yoast-scopes/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Yoast Plans Pricing](https://apis.io/plans/yoast/yoast-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Yoast Rate Limits](https://apis.io/rate-limits/yoast/yoast-rate-limits/)

#### FinOps (1)

What the API costs to run, by operation.

- [Yoast Finops](https://apis.io/finops/yoast/yoast-finops/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://yoast.com/)
- [Documentation](https://developer.yoast.com/customization/apis/)
- [Getting started](https://developer.yoast.com/customization/apis/using-apis-classes/)
- [API reference](https://developer.yoast.com/customization/apis/overview/)
- [Pricing](https://yoast.com/wordpress-seo-plugin/)
- [Support](https://yoast.com/help/)
- [Blog](https://developer.yoast.com/blog/)
- [Security](https://yoast.com/security-program/)
- [Terms of service](https://yoast.com/terms-of-service/)
- [Privacy policy](https://yoast.com/privacy-policy/)
- [GitHub](https://github.com/Yoast)
- [Status](https://status.yoast.com)

## API Evangelist rating

**Kin Score 62.9** — strong · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 78.6 |
| Contract quality | 58.0 |
| Contract governance | 45.5 |
| Operational transparency | 52.6 |
| Developer ergonomics | 73.2 |
| Access clarity | 52.6 |

**Agent readiness 37.0** — agent-ready

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | documented (partial credit) |
| MCP Server | — |
| Auth Clarity | served (partial credit) |
| Idempotency | — |
| Error Semantics | derived (partial credit) |
| OpenAPI Examples | documented (partial credit) |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | — |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | served (partial credit) |
| Protected Resource Metadata | — |
| Dynamic Client Registration | yes |
| Agentic Commerce | — |
| Pagination Ratio | — |
| Operation Distinctiveness | distinct |

**Regulatory alignment 40.2** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/yoast/](https://apis.io/providers/yoast/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Yoast: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/yoast/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
