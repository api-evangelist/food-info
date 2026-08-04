# Food Info

Harmonised nutrient data for reference foods, over a versioned REST API.

- **Developer:** https://food-info.org/developer
- **OpenAPI:** https://api.food-info.org/api/v1/openapi.json
- **Data sources:** https://food-info.org/data-sources
- **Dataset DOI:** https://doi.org/10.5281/zenodo.21527348
- **llms.txt:** https://food-info.org/llms.txt

Part of the [API Evangelist](https://apievangelist.com) network. Profiled 2026-08-04 from
[api-search/inbox#2](https://github.com/api-search/inbox/issues/2); every claim was fetched
first — see `X-Discovery` in `apis.yml`.

## What it does

Merges six food-composition datasets — **USDA FoodData Central**, **McCance & Widdowson's CoFID**,
**ANSES Ciqual**, **DTU Frida**, **AUSNUT** and **Open Food Facts** — into one schema, so a caller
queries nutrients across sources without reconciling each publisher's format.

Eight operations: nutrient catalogue, food search, food lookup, full nutrient panel, reverse
nutrient search (top and bottom foods), plus recipe parsing and per-line recipe analysis.

`X-Api-Key` header. Free tier of 10 requests a minute and 100 a day. HTTPS only, CORS disabled —
built for server-to-server use.

## Notes

**The dataset carries a citable Zenodo DOI**, which is unusual provenance for a commercial data
API and is recorded as a conformance artifact rather than buried in prose.

**They have an llms.txt they did not know about** — the submission stated none was published, but
`https://food-info.org/llms.txt` serves 8,462 bytes.

**0 of 8 operations carry an `operationId`.** Every one has a summary, so the spec is otherwise
well formed; adding operation ids is the cheapest improvement available and is what SDK
generators, MCP tool names and agent tool-calling key off.
