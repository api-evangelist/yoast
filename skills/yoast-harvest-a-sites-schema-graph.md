---
name: yoast-harvest-a-sites-schema-graph
description: >-
  Pull a whole WordPress site's Schema.org entity graph as JSON-L via the Yoast Schema
  Aggregator, discovering every available endpoint from the XML schemamap first instead
  of guessing post types and page numbers.
api: Yoast Schema Aggregator API
generated: '2026-08-13'
method: generated
source: openapi/yoast-schema-aggregator-openapi.yml
operations:
  - getSchemaMap
  - getAggregatedSchema
  - getAggregatedSchemaPage
---

# Harvest a site's Schema.org graph

## When to use this

You want the structured-data picture of an entire site — every Article, Product,
Organization, Person, LocalBusiness and so on — rather than one page's `<head>`. This is
the right tool for building a knowledge graph, a RAG corpus with real entity typing, or a
structured-data audit. Looping `getSeoHead` over every URL is the wrong tool.

## Steps

1. **Read the schemamap first** — `getSchemaMap`

   ```
   GET https://{site}/wp-json/yoast/v1/schema-aggregator/get-xml
   ```

   Returns XML listing every available schema endpoint on the site. This is the
   discovery document: it tells you which post types have aggregated schema and how many
   pages each has. Enumerate from it. Do not guess `post`, `page`, `product` and hope.

2. **Fetch a post type's graph** — `getAggregatedSchema`

   ```
   GET https://{site}/wp-json/yoast/v1/schema-aggregator/get-schema/post
   ```

3. **Walk pages by path segment** — `getAggregatedSchemaPage`

   ```
   GET https://{site}/wp-json/yoast/v1/schema-aggregator/get-schema/post/2
   ```

   Pagination here is a **path segment**, not a query parameter — unlike the `page` /
   `per_page` query parameters on `wp/v2/posts` and `wp/v2/pages`. Two different
   pagination styles in one provider; do not carry the wrong one across.

4. **Parse as JSON-L, not JSON.** The response is newline-delimited JSON — one
   Schema.org `@graph` per line. `JSON.parse` on the whole body will fail. Read it line
   by line, which also lets you stream a large site instead of buffering it.

## Rules and gotchas

- **You cannot set the page size.** Page size is controlled server-side by the site's
  `wpseo_schema_aggregator_per_page` PHP filter. There is no request parameter. Two sites
  can paginate identically-sized content completely differently, so always derive page
  count from the schemamap rather than assuming a constant.
- **The response is cached on the site.** If the site owner has just published and you
  are seeing stale output, they clear it with
  `wp yoast clear_schema_aggregator_cache <post_type>` — you cannot bust it from the API.
- **A 404 means "no schema for this post type or page", not "site down".** See
  `errors/yoast-problem-types.yml`.
- **Back off blindly on 429.** No `Retry-After`, no rate-limit headers anywhere in the
  Yoast surface. Harvesting a large site is exactly the workload that will trip a host's
  edge throttling, so pace requests and use exponential backoff with jitter.
- **This runs on the customer's host.** A full-site harvest is real load on somebody
  else's WordPress install. Rate-limit yourself even when they have not.
