---
name: yoast-audit-content-analysis-scores
description: >-
  Read the SEO, readability and inclusive-language analysis scores Yoast assigns to a
  site's most recently modified posts, using the WordPress Abilities API — the surface
  Yoast built specifically so an AI agent could see its analysis output.
api: Yoast SEO Abilities API
generated: '2026-08-13'
method: generated
source: openapi/yoast-abilities-api-openapi.yml
operations:
  - listAbilities
  - runGetSeoScores
  - runGetReadabilityScores
  - runGetInclusiveLanguageScores
---

# Audit a site's Yoast content-analysis scores

## When to use this

You want to know which recently edited posts on a WordPress site are failing Yoast's
checks, so you can prioritise what to rewrite. This is the intended agent path: Yoast
added it in Yoast SEO 27.5 (28 April 2026) explicitly to expose analysis results to
authenticated AI agents.

## Before you start

Three prerequisites, all of which fail silently if unmet:

- **WordPress 6.9 or higher** — the Abilities API is core, introduced in 6.9.
- **Yoast indexables enabled and fully built.** As of Yoast SEO 28.2, Yoast does not even
  register its abilities when indexables are disabled, so the abilities simply will not
  appear. If they are missing, have the site owner run `wp yoast index --reindex`
  (see `cli/yoast-cli.yml`).
- **Permission.** Every ability carries a permission check. Yoast does not publish which
  WordPress capability is required, so verify empirically as the identity you will use in
  production rather than as an administrator.

## Steps

1. **Discover what is actually registered** — `listAbilities`

   ```
   GET https://{site}/wp-json/wp-abilities/v1/abilities?category=yoast-seo
   ```

   Do this first, every time. It is the only reliable way to tell "Yoast is not
   installed" from "Yoast is installed but abilities are unregistered because indexables
   are off". Expect three names:
   `yoast-seo/get-seo-scores`, `yoast-seo/get-readability-scores`,
   `yoast-seo/get-inclusive-language-scores`.

2. **Run the SEO ability** — `runGetSeoScores`

   ```
   GET https://{site}/wp-json/wp-abilities/v1/abilities/yoast-seo/get-seo-scores/run?input[number_of_posts]=4
   ```

   `input[number_of_posts]` is an integer, 1–100, default 10. It is a cap, not a page
   size — there is no offset or cursor, so you cannot walk the whole site with it.

3. **Run the other two the same way** — `runGetReadabilityScores` and
   `runGetInclusiveLanguageScores`, same input, same shape.

4. **Interpret the scores.** Each result carries `title`, `score` and `label`. `score` is
   one of `na`, `bad`, `ok`, `good`. Only the SEO ability also returns
   `focus_keyphrase`, which may be `null` — a `bad` score with a `null` keyphrase usually
   means nobody set one, which is a different remediation from a keyphrase that is set
   but underused.

5. **Join to posts carefully.** Results are keyed by post **title**, not post id. To act
   on a post you must resolve the title yourself, e.g. via
   `GET /wp-json/wp/v2/posts?search={title}` — and titles are not unique, so treat any
   multi-hit as ambiguous rather than guessing. This is the sharpest edge on this API.

## Rules and gotchas

- **Read-only.** All three abilities are read-only. There is no Yoast ability to *set* a
  title, meta description or keyphrase. Every "edit Yoast meta with AI" product is a
  third-party WordPress plugin writing through some other route — do not attribute that
  capability to Yoast.
- **Scores describe the most recently modified posts only.** You cannot ask for a
  specific post, a date range, or a post type. If a page is not in the recent window, it
  is not reachable through this API.
- **`na` is not `bad`.** `na` means Yoast could not run the analysis (commonly no focus
  keyphrase, or an unsupported content shape). Reporting it as a failing score
  misrepresents the site.
- **No rate-limit headers, no idempotency keys, WordPress error envelope.** Same as every
  other Yoast surface — see `conventions/yoast-conventions.yml` and
  `errors/yoast-problem-types.yml`.
