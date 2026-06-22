---
name: store-locked-grocery-planner
description: Create store-specific, order-ready grocery lists from meal plans by locking one supermarket, store, delivery address, or shopping platform; verifying purchasable SKUs when possible; converting recipe raw/cooked/drained weights into package counts; handling substitutions, freshness, budget, and nutrition-label constraints. Use when users want a grocery list for a specific retailer such as Hema/Freshippo, Costco, Walmart, Aldi, Sam's Club, Instacart, Amazon Fresh, or a local supermarket, especially when they need exact product names, pack sizes, quantities, and a cart-ready plan.
---

# Store Locked Grocery Planner

## Purpose

Turn an existing meal plan or recipe list into a practical supermarket order tied to one specific retailer/store/location. The output should be close to a cart checklist: exact product names when verified, package counts, expected surplus, substitutions, storage timing, and confidence.

## Use Cases

Use this skill when the user asks to:

- Lock a grocery plan to one supermarket, store branch, delivery address, or online platform.
- Convert a meal plan into a cart-ready shopping list.
- Select exact SKUs, pack sizes, quantities, and substitutions.
- Match recipe raw weights, cooked weights, drained weights, or edible portions to store packages.
- Avoid unavailable, overpriced, high-sodium, high-sugar, allergen-containing, or inconvenient products.
- Split a weekly grocery order into main order and midweek freshness top-up.

## Accuracy Boundaries

- Do not claim a product is in stock at a specific store unless the source actually verifies it for that store/location and time.
- Do not fabricate SKU names, package sizes, prices, inventory, or delivery availability.
- If a retailer hides real-time inventory behind an app login, location gate, or account session, state that limitation and provide:
  - best official search terms,
  - likely retailer SKUs with confidence,
  - same-row substitutes,
  - a request for screenshots/cart export only if exact live verification is necessary.
- Treat prices, inventory, and package sizes as time-sensitive; browse or use user-provided screenshots for current data.
- Use the user's dietary restrictions, allergies, disliked foods, budget, freshness preferences, and nutrition constraints as hard filters.

## Required Inputs

Collect or infer conservatively:

- Retailer/platform name.
- Store branch, delivery address, city, ZIP/postcode, or nearest landmark.
- Meal plan or recipe list with ingredient quantities.
- Unit basis: raw weight, cooked weight, drained weight, edible portion, package count, or household unit.
- Number of days and servings.
- Budget and preferred brands, if any.
- Foods to avoid and acceptable substitutions.
- Freshness constraints, delivery schedule, refrigerator/freezer capacity.
- Nutrition-label constraints: sodium, saturated fat, sugar, protein, fiber, calories, allergens.

If the user has not provided a store/location, ask a concise clarifying question. If the user names a store and city/landmark, proceed with a clearly labeled assumption.

## Data Priority

Use sources in this order:

1. User-provided screenshots, product links, cart exports, or nutrition labels.
2. Official retailer app/site product pages for the specified store/location.
3. Official retailer search results or category pages.
4. Official brand product pages with matching pack size.
5. Public indexed product pages or nutrition databases that identify the retailer SKU.
6. Same-retailer generic product type without live SKU confirmation.
7. Other retailers as fallback only; label as not verified for the locked store.

Always cite web sources used. When using screenshots or user-provided data, cite them as user-provided.

## Workflow

### 1. Lock the Store

Record:

```json
{
  "retailer": "",
  "store_or_delivery_area": "",
  "city": "",
  "delivery_timing": "",
  "inventory_source": "official_live | official_public | user_screenshot | inferred_from_retailer | unavailable",
  "limitations": []
}
```

If live inventory is unavailable, continue with candidates but mark confidence honestly.

### 2. Normalize the Meal Plan

For every ingredient, normalize:

```json
{
  "ingredient": "",
  "required_amount": null,
  "required_unit": "g | ml | count",
  "basis": "raw | cooked | drained | edible | package",
  "recipe_use": "",
  "must_match": true,
  "acceptable_substitutions": []
}
```

Rules:

- Raw meat weights refer to edible raw weight unless the plan says bone-in or skin-on.
- Canned fish uses drained edible weight when the meal plan specifies drained fish.
- Rice, beans, oats, flour, nuts, seeds, and dry grains use dry weight unless stated otherwise.
- Produce uses raw purchased weight; account for peel, trimming, spoilage, and package rounding.
- Milk and liquids can be treated as ml approximately equal to g for shopping.

### 3. Search and Select SKUs

For each ingredient:

- Search the locked retailer first.
- Prefer unseasoned basic ingredients over marinated or heavily processed products.
- Prefer pack sizes that minimize waste while allowing recipe completion.
- Prefer nutrition labels matching the plan: low sodium soy sauce, water-packed fish, unsweetened oats, unsweetened milk, unflavored dairy, etc.
- For perishable foods, choose pack sizes compatible with storage and planned cooking day.

### 4. Convert to Package Counts

For each selected SKU, compute:

```text
package_count = ceil(required_amount / usable_amount_per_package)
surplus = package_count × usable_amount_per_package - required_amount
```

Use usable amount, not merely net weight:

- Bone-in meat usable amount may be 60-75% of package weight.
- Skin-on chicken has higher fat and lower edible lean yield.
- Canned fish should use drained weight when available.
- Leafy greens may lose 10-25% after trimming/cooking.
- Dry beans and rice are purchased dry; cooked yield is not used for package count unless the product is sold cooked.

### 5. Build Substitution Rows

Every fragile SKU should include a fallback:

- Same product, different pack size.
- Same ingredient, different brand.
- Equivalent ingredient from the same retailer.
- Nutrition-equivalent fallback if the exact ingredient is unavailable.

For substitutions, explain nutrition impact briefly:

- sodium higher/lower,
- fat higher/lower,
- protein lower/higher,
- omega-3 or calcium impact,
- cooking/prep impact.

### 6. Freshness and Delivery Timing

Decide whether to:

- buy everything in one order,
- split into main order and midweek top-up,
- choose frozen instead of fresh,
- buy shelf-stable products in larger packs,
- cook/freeze immediately after delivery.

For produce and fruit, avoid forcing a full week of fragile items when a midweek top-up or frozen version is better.

## Output Format

### A. Store Lock

- Retailer:
- Store/location:
- Inventory verification level:
- Limitations:

### B. Cart-Ready List

| Category | Exact product name | Pack size | Buy qty | Required | Surplus | Use in recipe | Confidence | Substitute |
|---|---|---:|---:|---:|---:|---|---|---|

Confidence:

- High: verified exact product, pack size, and availability for the locked store/location.
- Medium: exact retailer SKU or product page found, but live store inventory not verified.
- Low: likely search target or common SKU; user must verify in app.

### C. Recipe Mapping

| Recipe/module | Products used | Amount used | Notes |
|---|---|---:|---|

### D. Order Timing

- Main order:
- Midweek top-up:
- Freeze immediately:
- Keep unopened:

### E. Label Checks

| Product type | Label field to check | Pass condition |
|---|---|---|

Examples:

- Fish can: sodium per 100g, drained weight, oil/water pack.
- Soy sauce: sodium per serving.
- Milk: unsweetened, low-fat/skim if the plan assumes low fat.
- Oats: unsweetened, no added granola/sugar.
- Meat: unseasoned, raw, no marinade.

### F. Gaps and User Actions

List only meaningful gaps:

- exact live inventory unavailable,
- uncertain drained weight,
- pack size mismatch,
- screenshot needed for true one-click exactness.

## Agent Behavior Rules

- Provide a usable grocery order, not only shopping principles.
- Lock one retailer at a time unless the user asks for comparison.
- Do not mix retailers in the main cart unless explicitly allowed.
- Prefer exact product names over generic categories, but do not invent certainty.
- Include package counts and surplus for every cart item.
- When the store's official data is unavailable, label candidates as candidates.
- If the user wants true exact carting for an app-only retailer, ask for screenshots/cart export only after exhausting public sources.
- Keep meal-plan nutrition consistent when substituting products.
