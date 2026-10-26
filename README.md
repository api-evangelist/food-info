# Food Info (food-info)

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
