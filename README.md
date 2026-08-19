# Food Info (food-info)

Food Info serves harmonised nutrient data for reference foods over a versioned REST API. It merges six food-composition datasets — USDA FoodData Central, McCance & Widdowson's CoFID, ANSES Ciqual, DTU Frida, AUSNUT and Open Food Facts — into a single schema, so a caller can query nutrients across sources without reconciling each publisher's format. Endpoints cover food search, a full nutrient panel per food, a nutrient catalogue, reverse nutrient search for the richest and poorest reference foods, and recipe parsing and analysis that resolves raw ingredient lines into per-line nutrition. Authentication is an X-Api-Key header, with a free tier of 10 requests a minute and 100 a day. HTTPS only and CORS disabled, so it is built for server-to-server use. The underlying dataset carries a citable Zenodo DOI, which is unusual provenance for a commercial data API.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/food-info/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/food-info/refs/heads/main/apis.yml)

## Scope

- **Type:** Index
- **Position:** Producing
- **Access:** 3rd-Party

## Tags

- Nutrition
- Food
- Food Composition
- Nutrients
- Data
- Open Data
- Dietetics
- Recipes
- Health
- Research

## Timestamps

- **Created:** 2026-08-04
- **Modified:** 2026-08-04

## APIs

### Food Info API V1 API

The ApiV1 API from Food Info — 6 operation(s) for apiv1.

- **Human URL:** [https://food-info.org/developer](https://food-info.org/developer)
- **Base URL:** `https://api.food-info.org`

#### Tags

- ApiV1

#### Properties

- [OpenAPI](openapi/food-info-apiv1-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/food-info-apiv1-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/food-info-apiv1-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [X- Open A P I- Source](https://api.food-info.org/api/v1/openapi.json)
- [Documentation](https://food-info.org/developer)
- [Authentication](authentication/food-info-authentication.yml)
- [Plans](plans/food-info-plans.yml)
- [Conformance](conformance/food-info-data-provenance.yml)
- [X- Data Sources](https://food-info.org/data-sources)
- [X- Dataset D O I](https://doi.org/10.5281/zenodo.21527348)
- [Terms of Service](https://food-info.org/terms-conditions)
- [Privacy Policy](https://food-info.org/privacy-policy)
- [Llms Text](https://food-info.org/llms.txt)
- [Examples](examples/food-info-examples.yml)
- [Rate Limits](rate-limits/food-info-rate-limits.yml)
- [Error Catalog](errors/food-info-problem-types.yml)
- [Conventions](conventions/food-info-conventions.yml)
- [Data Model](data-model/food-info-data-model.yml)
- [Tool Crosswalk](mcp/food-info-tool-crosswalk.yml)

### Food Info Recipes API API

The RecipesApi API from Food Info — 2 operation(s) for recipesapi.

- **Human URL:** [https://food-info.org/developer](https://food-info.org/developer)
- **Base URL:** `https://api.food-info.org`

#### Tags

- RecipesApi

#### Properties

- [OpenAPI](openapi/food-info-recipesapi-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/food-info-recipesapi-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/food-info-recipesapi-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [X- Open A P I- Source](https://api.food-info.org/api/v1/openapi.json)
- [Documentation](https://food-info.org/developer)
- [Authentication](authentication/food-info-authentication.yml)
- [Plans](plans/food-info-plans.yml)
- [Conformance](conformance/food-info-data-provenance.yml)
- [X- Data Sources](https://food-info.org/data-sources)
- [X- Dataset D O I](https://doi.org/10.5281/zenodo.21527348)
- [Terms of Service](https://food-info.org/terms-conditions)
- [Privacy Policy](https://food-info.org/privacy-policy)
- [Llms Text](https://food-info.org/llms.txt)
- [Examples](examples/food-info-examples.yml)
- [Rate Limits](rate-limits/food-info-rate-limits.yml)
- [Error Catalog](errors/food-info-problem-types.yml)
- [Conventions](conventions/food-info-conventions.yml)
- [Data Model](data-model/food-info-data-model.yml)
- [Tool Crosswalk](mcp/food-info-tool-crosswalk.yml)

## Common Properties

- [Agentic Access](agentic-access/food-info-agentic-access.yml)
- [Domain Security](security/food-info-domain-security.yml)
- [Website](https://food-info.org)
- [Documentation](https://food-info.org/developer)
- [Terms of Service](https://food-info.org/terms-conditions)
- [Privacy Policy](https://food-info.org/privacy-policy)
- [Llms Text](https://food-info.org/llms.txt)
- [Authentication](authentication/food-info-authentication.yml)
- [Plans](plans/food-info-plans.yml)
- [Conformance](conformance/food-info-data-provenance.yml)
- [Conformance](conformance/food-info-conformance.yml)
- [Developer Portal](https://food-info.org/developer)
- [Support](https://food-info.org/contact)
- [Well Known](well-known/food-info-well-known.yml)
- [Security Txt](well-known/food-info-security.txt)
- [Vulnerability Disclosure](security/food-info-vulnerability-disclosure.yml)
- [Security](https://food-info.org/.well-known/security.txt)
- [Rate Limits](rate-limits/food-info-rate-limits.yml)
- [Error Catalog](errors/food-info-problem-types.yml)
- [Conventions](conventions/food-info-conventions.yml)
- [Lifecycle](lifecycle/food-info-lifecycle.yml)
- [Data Model](data-model/food-info-data-model.yml)
- [M C P Server](mcp/food-info-mcp.yml)
- [Tool Crosswalk](mcp/food-info-tool-crosswalk.yml)
- [Agent Skill](skills/_index.yml)
- [Overlay](overlays/food-info-overlay.yaml)
- [Examples](examples/food-info-examples.yml)
- [L L Ms Txt](llms/food-info-llms.txt)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
