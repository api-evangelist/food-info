---
name: Analyse the nutrition of a recipe
description: Turn raw ingredient lines into per-serving and per-100 g nutrition, with per-line source attribution and review flags.
api: openapi/food-info-openapi.json
operations: [parseRecipeIngredients, analyzeRecipeNutrition, getFoodNutrientPanel]
generated: '2026-08-04'
method: generated
source: openapi/food-info-openapi.json
---

# Analyse the nutrition of a recipe

Use this when you have a recipe as free text — "2 large eggs", "150 g plain flour", "a splash of
olive oil" — and need real nutrition numbers out of it.

## Before you start

- Base URL `https://api.food-info.org`, `X-Api-Key` header, `Content-Type: application/json`.
- Both operations are POST but **neither persists anything**. They are calculators: the same body
  returns the same result, and a retry is safe — it just costs another call against the quota. There
  is no idempotency key and none is needed.

## Steps

1. **Parse first if you need to show your working.** `parseRecipeIngredients` —
   `POST /api/v1/recipes/parse` with `{ "lines": ["2 large eggs", "150 g plain flour"] }`. Returns
   `ParsedIngredient[]` — the structured quantity/unit/food breakdown with a `unitKind` of `Mass`,
   `Volume`, `Count`, `Vague` or `None`. **No catalogue match happens here and no nutrition is
   computed.** Use it to show a user how their lines were understood, or to catch a `Vague` line
   before you analyse.
2. **Analyse.** `analyzeRecipeNutrition` — `POST /api/v1/recipes/analyze` with
   `{ "lines": [...], "region": "GB", "servings": 4 }`. `region` sets the regional weighting for
   which national dataset an ingredient resolves against; `servings` divides the totals.
3. **Read `RecipeAnalysis` in this order:**
   - `ingredients[]` — one `IngredientResult` per line: `raw`, `foodPhrase`, `foodId`,
     `matchedDescription`, `source`, `grams`, `confidence`, `needsReview`, `note`.
   - `perServing` and `per100g` — the `NutritionFacts` headline numbers.
   - `nutrientGroups[]` — the grouped detail rows.
4. **Check the flags before you report anything.** Any line with `needsReview: true` or a low
   `confidence` did not resolve cleanly. Surface it to the user rather than silently folding it into
   the total — the totals are only as good as the weakest matched line.
5. **Optional — verify a match.** `foodId` on an `IngredientResult` is a catalogue id, so
   `getFoodNutrientPanel` (`GET /api/v1/foods/{foodId}/panel`) shows exactly which reference food a
   line was priced against.

## Rules

- Never present recipe totals without saying how many lines needed review.
- `grams` is the resolved mass the analysis actually used. If a line was `Vague` or `Count`-based,
  that mass was inferred — flag it.
- Attribute the source dataset per line from `IngredientResult.source`.
- These are reference values, not dietary or medical advice.

## Errors

- `400` — malformed body, empty `lines`, or a non-integer `servings`. `ProblemDetails` body.
- `401` — missing/invalid `X-Api-Key`, empty body.
- Analysis is the most expensive call on the surface. Parse locally-cached recipes once and store the
  result rather than re-analysing on every render — the free tier is 100 calls a day.
