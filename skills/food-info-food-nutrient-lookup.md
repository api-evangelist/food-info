---
name: Look up the nutrient panel for a food
description: Resolve a food name to a Food Info catalogue id and return its full nutrient panel, with the correct reference-intake basis.
api: openapi/food-info-openapi.json
operations: [searchFoods, getFood, getFoodNutrientPanel]
generated: '2026-08-04'
method: generated
source: openapi/food-info-openapi.json
---

# Look up the nutrient panel for a food

Use this when someone asks what is in a food — calories, macros, vitamins, minerals — and you have a
name, not an id.

## Before you start

- Base URL: `https://api.food-info.org`
- Send `X-Api-Key: <key>` on every request. There is no other auth, no OAuth, no bearer token.
- HTTPS only, and CORS is disabled — call this server-side, never from a browser.
- Quotas are per account, not per key: 10 req/min and 100/day on the free tier, 60/min and
  10,000/day on Practitioner. Read `X-RateLimit-Limit-Minute`, `X-RateLimit-Limit-Day` and
  `X-RateLimit-Tier` off the response. There is no `Remaining` header, so count your own calls.

## Steps

1. **Resolve the food.** `searchFoods` — `GET /api/v1/foods/search?q={name}`. Optional `home_nation`
   biases results toward that country's source dataset; optional `limit` defaults to 25. You get back
   an array of `{ id, description, ndbNumber }`. Pick the `id` whose `description` actually matches
   what was asked; do not assume the first hit.
2. **Optional — confirm the food.** `getFood` — `GET /api/v1/foods/{id}` returns the summary
   including `dataType`, so you can tell a Foundation or SR Legacy reference food from a Branded or
   Open Food Facts entry before you quote numbers.
3. **Get the panel.** `getFoodNutrientPanel` — `GET /api/v1/foods/{id}/panel`. Pass `source` to pick
   the reference-intake basis: `UK RI` (EU Reg. 1169/2011, the default) or `FDA 2016` for US Daily
   Values. Pass `portionId` to switch serving; the available servings come back on the panel itself
   as `availableServings`.
4. **Read the response correctly.** `groups[]` are titled nutrient groups, each with `rows[]`. All
   amounts are **per 100 g** unless you are reading the per-serving column. `source` names which
   national dataset the values came from — quote it when you report the numbers.

## Rules

- Always cite the `source` dataset with any nutrient figure. Merging six national datasets is the
  point of this API; a number without its source is not usable in a citation.
- `%` reference-intake values are basis-dependent. If you did not set `source`, you are reporting UK
  Reference Intakes, not US Daily Values — say so.
- These are reference values for foods, not medical or dietary advice, and the provider's terms say
  so explicitly.

## Errors

- `400` — bad query on `searchFoods`. Body is `ProblemDetails` (`type`/`title`/`status`/`detail`/
  `instance`) as `application/json`.
- `404` — the `id` is not in the catalogue. Re-resolve with `searchFoods`; do not retry the same id.
- `401` — missing or invalid `X-Api-Key`. **The body is empty** — there is no error document on auth
  failure, so branch on the status code alone.
- Over-quota behaviour is not declared in the spec. Treat any unexpected non-2xx as terminal, back
  off, and do not hot-retry: every attempt is billed against the daily quota.
