---
name: yoast-read-seo-metadata-for-a-url
description: >-
  Retrieve every piece of SEO metadata Yoast produces for a single URL on a WordPress
  site — title, meta description, canonical, robots directives, Open Graph, Twitter Card
  and the full Schema.org JSON-LD graph — in one call, for headless rendering or an SEO
  audit.
api: Yoast SEO Head API
generated: '2026-08-13'
method: generated
source: openapi/yoast-seo-head-api-openapi.yml
operations:
  - getSeoHead
---

# Read SEO metadata for a URL

## When to use this

The site runs WordPress with Yoast SEO, and you need the `<head>` for a page you are
rendering yourself (a headless front end), or you are auditing what the site tells search
engines about a page. This is the one call that returns everything at once.

## Before you start

- **The base URL is the customer's site, not Yoast's.** Yoast ships plugin code; there is
  no `api.yoast.com`. The base is `https://{site}/wp-json`. If you do not know the site,
  you cannot call this API.
- **There is no Yoast API key.** For public content this route needs no credential. See
  `authentication/yoast-authentication.yml` — anything requiring a login rides WordPress
  authentication (cookie + nonce, or an Application Password), never a Yoast one.
- **It is read-only.** Yoast's own docs are explicit: the REST API "doesn't currently
  support POST or PUT calls to update the data". Do not attempt writes.

## Steps

1. **Fetch the head** — `getSeoHead`

   ```
   GET https://{site}/wp-json/yoast/v1/get_head?url=https://{site}/blog/my-post/
   ```

   `url` is required and must be the full absolute URL of the page.

2. **Read the response.** Three fields:
   - `html` — the escaped, prefabricated meta tags and JSON-LD, ready to inject into
     `<head>`. Use this when you are rendering.
   - `json` — the same information as structured data (`SeoMetadata`). Use this when you
     are analysing. Requires Yoast SEO 16.7+ on the site.
   - `status` — the HTTP status of the *requested URL*, not of your API call. A `200`
     from the API can carry `status: 404` for a page that does not exist.

3. **Check `status` before trusting the payload.** Yoast returns full responses for
   non-200 scenarios, including legitimate 404s, so a naive integration will happily
   render the metadata of a 404 page. Branch on `json.status` / `status`.

4. **Take the schema graph from `json.schema`** if you need structured data. For a whole
   site rather than one page, switch to the Schema Aggregator instead of looping this
   endpoint — see `yoast-harvest-a-sites-schema-graph`.

## Rules and gotchas

- **Errors use the WordPress envelope, not Problem Details.** A failure returns
  `{"code","message","data":{"status"}}` with `application/json`. There is no
  `application/problem+json` and no error `type` URI. See
  `errors/yoast-problem-types.yml`.
- **No rate-limit headers exist.** Yoast emits no `RateLimit-*` or `X-RateLimit-*`, and
  no `Retry-After`. Throttling belongs to the customer's own host and its edge. On a 429,
  back off exponentially with jitter — you have no budget to read. See
  `rate-limits/yoast-rate-limits.yml`.
- **No idempotency keys.** Irrelevant here because this is a GET, but do not assume they
  exist anywhere else in the Yoast surface — they do not. See
  `conventions/yoast-conventions.yml`.
- **Output varies per site.** Site owners can change what Yoast emits through dozens of
  `wpseo_*` PHP filters. Two Yoast sites can return materially different payloads from
  this same route, and nothing in the contract signals it. Do not hard-code assumptions
  about which optional fields are present.
