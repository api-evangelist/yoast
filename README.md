# Yoast (yoast)

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

Yoast is the maker of the world's most popular WordPress SEO plugin, active on over 13 million sites. Yoast provides developer APIs for integrating SEO metadata, structured data (Schema.org), meta tags, sitemaps, and SEO analysis into headless WordPress sites and third-party platforms. Key products include Yoast SEO Free, Yoast SEO Premium, WooCommerce SEO, Local SEO, Video SEO, and News SEO.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/yoast/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/yoast/refs/heads/main/apis.yml)

## Scope

- **Type:** Index
- **Position:** Consumer
- **Access:** 3rd-Party

## Tags

- SEO
- WordPress
- Content Optimization
- Schema
- Metadata

## Timestamps

- **Created:** 2025-01-14
- **Modified:** 2026-05-19

## APIs

### Yoast REST API

The Yoast REST API returns all SEO metadata (meta tags, Schema.org JSON-LD, canonical URLs, Open Graph, Twitter Card data, and robots directives) for any URL or post on a WordPress site. It extends the native WordPress WP-JSON REST API and also provides a dedicated endpoint at /yoast/v1/get_head. The API is read-only and designed for headless WordPress implementations.

- **Human URL:** [https://developer.yoast.com/customization/apis/rest-api/](https://developer.yoast.com/customization/apis/rest-api/)
- **Base URL:** `https://{your-site}/wp-json`

#### Tags

- SEO
- REST API
- Metadata
- WordPress
- Headless

#### Properties

- [Documentation](https://developer.yoast.com/customization/apis/rest-api/)
- [OpenAPI](https://raw.githubusercontent.com/api-evangelist/yoast/refs/heads/main/openapi/yoast-rest-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/yoast-rest.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/yoast-rest.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Yoast Surfaces API

The Yoast Surfaces API provides a PHP interface for retrieving SEO metadata programmatically within WordPress. It exposes the YoastSEO() surface with methods to get metadata for the current page, a specific post by ID, or a given URL. Returns titles, descriptions, Schema arrays, canonical URLs, robots directives, OpenGraph, and Twitter card data.

- **Human URL:** [https://developer.yoast.com/customization/apis/surfaces-api/](https://developer.yoast.com/customization/apis/surfaces-api/)
- **Base URL:** `https://{your-site}`

#### Tags

- SEO
- PHP API
- Metadata
- WordPress

#### Properties

- [Documentation](https://developer.yoast.com/customization/apis/surfaces-api/)
- [Postman Collection](collections/yoast-rest.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/yoast-rest.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Yoast Metadata API

The Yoast Metadata API provides a PHP interface to add, alter, or remove metadata in the <head> of a WordPress document. Developers can hook into Yoast's meta tag output pipeline to customize titles, descriptions, robots directives, Open Graph tags, and other head elements programmatically.

- **Human URL:** [https://developer.yoast.com/customization/apis/metadata-api/](https://developer.yoast.com/customization/apis/metadata-api/)
- **Base URL:** `https://{your-site}`

#### Tags

- SEO
- PHP API
- Metadata
- WordPress

#### Properties

- [Documentation](https://developer.yoast.com/customization/apis/metadata-api/)
- [Postman Collection](collections/yoast-rest.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/yoast-rest.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Yoast Schema API

The Yoast Schema API provides a PHP interface for customizing the Schema.org JSON-LD structured data output generated by Yoast SEO. Developers can add, remove, or modify schema pieces such as Organization, WebSite, Article, BreadcrumbList, and more to control how search engines interpret page content.

- **Human URL:** [https://developer.yoast.com/customization/apis/schema-api/](https://developer.yoast.com/customization/apis/schema-api/)
- **Base URL:** `https://{your-site}`

#### Tags

- SEO
- Schema.org
- Structured Data
- PHP API
- WordPress

#### Properties

- [Documentation](https://developer.yoast.com/customization/apis/schema-api/)
- [Postman Collection](collections/yoast-rest.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/yoast-rest.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [LinkedIn](https://www.linkedin.com/company/yoast-com)
- [Website](https://yoast.com/)
- [Developer  Portal](https://developer.yoast.com/)
- [Documentation](https://developer.yoast.com/customization/apis/)
- [GitHub Organization](https://github.com/Yoast)
- [Blog](https://developer.yoast.com/blog/)
- [Pricing](https://yoast.com/wordpress-seo-plugin/)
- [Plugin](https://wordpress.org/plugins/wordpress-seo/)
- [OpenAPI](https://raw.githubusercontent.com/api-evangelist/yoast/refs/heads/main/openapi/yoast-rest-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Vocabulary](https://raw.githubusercontent.com/api-evangelist/yoast/refs/heads/main/vocabulary/yoast-vocabulary.yml)
- [Integrations](https://yoast.com/integrations/)
- [L L Ms Txt](https://yoast.com/llms.txt)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
