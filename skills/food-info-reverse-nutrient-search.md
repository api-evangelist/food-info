---
name: Find the foods highest or lowest in a nutrient
description: Discover a nutrientId from the catalogue, then rank reference foods richest or poorest in that nutrient per 100 g.
api: openapi/food-info-openapi.json
operations: [listNutrients, listTopFoodsByNutrient, listBottomFoodsByNutrient, getFoodNutrientPanel]
generated: '2026-08-04'
method: generated
source: openapi/food-info-openapi.json
---

# Find the foods highest or lowest in a nutrient

Use this for "what should I eat for iron?" and for its inverse, "what can I eat that is low in
potassium?" — the restriction case matters as much as the seeking case.

## Before you start

- Base URL `https://api.food-info.org`, `X-Api-Key` header, server-side only.
- Budget your calls: the free tier is 10/min and 100/day per account.

## Steps

1. **Get the nutrient id.** `listNutrients` — `GET /api/v1/nutrients` returns the whole catalogue as
   `{ id, name, unit, category, rank, hasRda }`. Match on `name`, and keep `unit` — you need it to
   render the amounts. `hasRda` tells you whether a reference intake exists for this nutrient at all.
   Cache this list; it is small and stable, and re-fetching it wastes quota.
2. **Rank the foods.**
   - Richest: `listTopFoodsByNutrient` — `GET /api/v1/nutrients/{nutrientId}/top-foods`
   - Poorest: `listBottomFoodsByNutrient` — `GET /api/v1/nutrients/{nutrientId}/bottom-foods`
   - Both take `home_nation` (regional weighting) and `limit` (default 25).
3. **Read the result.** `TopByNutrientDto` carries `nutrient` (the `NutrientRefDto` you ranked on)
   and `results[]` of `{ foodId, description, amount }`. `amount` is **per 100 g**, highest first for
   top-foods and lowest first for bottom-foods.
4. **Optional — go deeper on a hit.** `foodId` is a catalogue id, so hand it straight to
   `getFoodNutrientPanel` (`GET /api/v1/foods/{foodId}/panel`) for the full panel of any food in the
   ranking.

## Rules

- Per 100 g is not per portion. A ranking by per-100 g density will put spices and dried goods at the
  top of many nutrients; say which basis you are ranking on before presenting the list.
- Do not invent nutrient ids. They come from `listNutrients` and nowhere else — a guessed id returns
  `404`, not a near match.
- For a restriction question (low sodium, low potassium, low phosphorus) use `bottom-foods`. Do not
  invert a top-foods list yourself — it ranks the wrong end of the catalogue.

## Errors

- `400` — malformed `limit` or `home_nation`. `ProblemDetails` body as `application/json`.
- `404` — no such `nutrientId`. Re-resolve from `listNutrients`.
- `401` — missing/invalid key, empty body.
