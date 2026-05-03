# Yoast

Yoast is the maker of the world's most popular WordPress SEO plugin, active on over 13 million sites. Yoast provides developer APIs for integrating SEO metadata, structured data (Schema.org), meta tags, sitemaps, and SEO analysis into headless WordPress sites and third-party platforms.

**Website:** https://yoast.com/  
**Developer Portal:** https://developer.yoast.com/  
**GitHub:** https://github.com/Yoast  

## APIs

| API | Description | Documentation |
|-----|-------------|---------------|
| [Yoast REST API](openapi/yoast-rest-openapi.yml) | Returns SEO metadata for any URL or post via WP-JSON | [Docs](https://developer.yoast.com/customization/apis/rest-api/) |
| Yoast Surfaces API | PHP interface for retrieving SEO metadata within WordPress | [Docs](https://developer.yoast.com/customization/apis/surfaces-api/) |
| Yoast Metadata API | PHP interface to add/alter/remove head metadata | [Docs](https://developer.yoast.com/customization/apis/metadata-api/) |
| Yoast Schema API | PHP interface for customizing Schema.org JSON-LD output | [Docs](https://developer.yoast.com/customization/apis/schema-api/) |

## Artifacts

### OpenAPI Specifications
- [yoast-rest-openapi.yml](openapi/yoast-rest-openapi.yml) — Yoast REST API (SEO head, posts, pages)

### JSON Schema
- [yoast-seo-metadata-schema.json](json-schema/yoast-seo-metadata-schema.json) — SEO metadata schema

### JSON Structure
- [yoast-seo-metadata-structure.json](json-structure/yoast-seo-metadata-structure.json) — SEO metadata field documentation

### JSON-LD
- [yoast-context.jsonld](json-ld/yoast-context.jsonld) — Linked Data context for SEO metadata

### Examples
- [yoast-rest-get-seo-head-example.json](examples/yoast-rest-get-seo-head-example.json) — Get SEO head for URL
- [yoast-rest-get-post-seo-example.json](examples/yoast-rest-get-post-seo-example.json) — Get post with SEO data

### Spectral Rules
- [yoast-rules.yml](rules/yoast-rules.yml) — Spectral linting rules for Yoast API conventions

### Naftiko Capabilities
- [seo-metadata.yaml](capabilities/seo-metadata.yaml) — SEO metadata workflow capability (5 tools)
- [shared/yoast-rest.yaml](capabilities/shared/yoast-rest.yaml) — Shared Yoast REST API definition

### Vocabulary
- [yoast-vocabulary.yml](vocabulary/yoast-vocabulary.yml) — SEO domain vocabulary

## Key Features

- **Read-only REST API** — Returns all SEO metadata for any WordPress URL
- **Headless WordPress** — Designed for decoupled frontend architectures
- **Schema.org** — Automated structured data generation (Article, WebPage, Organization, etc.)
- **Open Graph** — Social sharing metadata for Facebook, LinkedIn, and more
- **Twitter Cards** — Twitter/X social sharing metadata
- **XML Sitemaps** — Auto-generated for all post types and taxonomies
- **AI-Powered** — AI Optimize and AI Generate for titles and meta descriptions
- **WooCommerce SEO** — Product and category SEO for e-commerce

## Use Cases

- Headless WordPress SEO metadata retrieval
- Content auditing and SEO monitoring
- Social sharing preview optimization
- Structured data validation and testing
- Multi-site SEO management

## Maintainers

**FN:** Kin Lane  
**Email:** kin@apievangelist.com
