# Examples

This document shows how the two skills can be used separately or as a combined workflow.

## Example 1: Carb-Cycling Batch Meal Plan

Prompt:

```text
Use $carb-cycle-batch-meal-planner.
I am 24, male, 182cm, 88kg, and train six days per week:
Monday back, Tuesday chest, Wednesday arms, Thursday shoulders, Friday chest, Saturday back.
I play badminton for about 90 minutes on Wednesday and Saturday nights and do 30 minutes of fasted cardio every morning.
Goal: fat loss while keeping muscle.
I dislike broccoli, chicken breast, and yogurt.
I can buy beef, chicken thighs, rice, oats, potatoes, vegetables, tofu, eggs, milk, black beans, red beans, soybeans, chickpeas, and canned fish.
Build a one-week carb-cycling meal plan. Use raw weights for shopping and include fiber, Omega-3, potassium, sodium, calcium, and magnesium checks.
```

Representative result excerpt:

```text
BMR: about 1903 kcal
Estimated TDEE: about 3140 kcal
Weekly target: about 2550-2600 kcal/day
Protein target: about 170-190g/day
High-carb days: Wednesday and Saturday
Medium-carb days: Monday, Tuesday, Thursday, Friday
Low-carb day: Sunday
```

Daily macro excerpt:

| Day | Training | Carb Type | Calories | Protein | Carbs | Fat | Fiber |
|---|---|---|---:|---:|---:|---:|---:|
| Monday | Back + cardio | Medium | 2425 | 174g | 284g | 68g | 36g |
| Tuesday | Chest + cardio | Medium | 2510 | 187g | 288g | 77g | 37g |
| Wednesday | Arms + badminton | High | 2990 | 190g | 413g | 68g | 41g |
| Saturday | Back + badminton | High | 2830 | 169g | 420g | 55g | 38g |
| Sunday | Recovery | Low | 2225 | 170g | 209g | 89g | 38g |

Meal modules:

| Module | Raw / Dry Weights | Notes |
|---|---|---|
| Breakfast | oats, milk, eggs, chia seeds, berries or banana | Yogurt-free version; berries can be frozen. |
| Rice-bean base | dry rice plus dry black beans, red beans, soybeans, or chickpeas | Beans are weighed dry before soaking. |
| Tomato mushroom beef | lean beef, tomatoes, mushrooms, onion, spinach | Batch-cooked for lunch/dinner boxes. |
| Ginger garlic chicken thigh | boneless skinless chicken thigh, carrots, bell pepper, leafy greens | Badminton pre-meal portions use less oil and less fiber. |
| Tofu egg tomato | firm tofu, eggs, tomatoes, spinach, mushrooms | Supports calcium and plant-protein diversity. |
| Fish potato bowl | canned mackerel/salmon/tuna, potatoes, tomatoes, greens | Prefer water-packed fish; check sodium and drained weight. |

Nutrition loop excerpt:

| Nutrient | Target | Plan Average | Status |
|---|---:|---:|---|
| Calories | 2550-2600 kcal/day | about 2570 | OK |
| Protein | 165-190g/day | about 177g | OK |
| Fiber | 35-40g/day | about 38g | OK |
| Sodium | below 2300mg/day when possible | about 1600mg before variable labels | OK if low-sodium condiments are used |
| Calcium | at least 1000mg/day | about 1900mg | OK |
| Magnesium | at least 400mg/day | about 670mg | OK |
| Omega-3 | ALA plus fish-based EPA/DHA | covered by chia and fish | OK |

## Example 2: Store-Locked Grocery Order

Prompt:

```text
Use $store-locked-grocery-planner.
Take the weekly plan above and lock the order to Jiajiayue supermarket near Jinan Yinfeng Jiuxi City.
I want a delivery-shopping list with product names, package sizes, buy counts, required amounts, surplus, and substitutions.
```

Representative result excerpt:

| Category | Product Target | Pack Size | Buy Qty | Required | Surplus | Confidence | Substitute |
|---|---|---:|---:|---:|---:|---|---|
| Chicken | unseasoned boneless skinless chicken thigh | 300g | 5 | 1290g | about 210g | Low to Medium unless app-verified | chicken leg quarters, 1.8-2kg, self-trim |
| Beef | lean beef strips / tenderloin / round | 250g | 4 | 960g | about 40g | Low to Medium | unseasoned lean beef slices |
| Eggs | fresh eggs | 10-count | 2 | 17 eggs | 3 eggs | Medium | any plain fresh egg pack |
| Milk | unsweetened low-fat or skim milk | 250ml x 24 | 1 case | 4700ml | about 1300ml | Medium | 950ml low-fat milk x 5 |
| Tofu | firm tofu / northern tofu | 300-400g | 3 | 840g | 60-360g | Low to Medium | firm tofu, not silken tofu |
| Canned fish | water-packed mackerel / salmon / tuna | 150-200g | 2 | 240g drained | depends on drained weight | Low until label verified | water-packed tuna |

The grocery skill should explicitly state when exact live inventory is not available from public sources. For app-only retailers, exactness requires user-provided product screenshots, cart exports, or in-app links.

## Combined Workflow

1. Use `carb-cycle-batch-meal-planner` to generate the nutritional plan and ingredient quantities.
2. Convert every ingredient to raw, dry, drained, or edible weight.
3. Use `store-locked-grocery-planner` to lock the order to one retailer.
4. Check label-dependent items:
   - canned fish sodium, oil/water pack, drained weight,
   - milk fat and sugar,
   - soy sauce sodium,
   - oats added sugar,
   - meat marinade status.
5. Split the order if freshness matters:
   - main order for meat, milk, eggs, grains, beans, canned fish, sturdy vegetables,
   - midweek top-up for leafy greens, bananas, grapes, or fragile fruit.

## Notes for Chinese Grocery Platforms

For platforms such as Hema/Freshippo, Jiajiayue, Meituan, JD Daojia, and Ele.me, live SKU availability is often location- and account-gated. The store-locked skill should produce an order-ready candidate list, but must not state that a product is definitely in stock unless the exact store-specific product page or user-provided app data confirms it.
