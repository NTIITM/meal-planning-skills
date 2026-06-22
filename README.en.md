# Meal Planning Codex Skills

English | [中文](README.md)

Two Codex skills for turning fitness meal-planning requests into executable weekly systems:

- `carb-cycle-batch-meal-planner`: builds carb-cycling weekly meal plans, batch prep schedules, storage plans, and nutrition checks.
- `store-locked-grocery-planner`: turns a meal plan into a store-specific grocery order with product names, pack counts, substitutions, and confidence labels.

The skills are designed to work together. First generate a nutrition-aware weekly plan, then lock the grocery order to one retailer or delivery area.

## Skills

| Skill | Purpose |
|---|---|
| [`carb-cycle-batch-meal-planner`](skills/carb-cycle-batch-meal-planner/SKILL.md) | Create a carb-cycling weekly menu from body metrics, training schedule, food preferences, purchasable ingredients, cooking capacity, storage, and nutrition targets. |
| [`store-locked-grocery-planner`](skills/store-locked-grocery-planner/SKILL.md) | Convert recipes or meal plans into a retailer-specific cart with package counts, surplus, substitutions, live-inventory caveats, and label checks. |

## Install

Clone the repository and copy the desired skill folders into your Codex skills directory.

PowerShell:

```powershell
git clone https://github.com/NTIITM/meal-planning-skills.git
Copy-Item -Recurse .\meal-planning-skills\skills\carb-cycle-batch-meal-planner "$env:USERPROFILE\.codex\skills\"
Copy-Item -Recurse .\meal-planning-skills\skills\store-locked-grocery-planner "$env:USERPROFILE\.codex\skills\"
```

Bash:

```bash
git clone https://github.com/NTIITM/meal-planning-skills.git
cp -R meal-planning-skills/skills/carb-cycle-batch-meal-planner ~/.codex/skills/
cp -R meal-planning-skills/skills/store-locked-grocery-planner ~/.codex/skills/
```

If `CODEX_HOME` is set, copy into `$CODEX_HOME/skills` instead.

## Quick Usage

Use the carb-cycle skill first:

```text
Use $carb-cycle-batch-meal-planner.
I am 24, male, 182cm, 88kg. I train 6 days per week and play badminton on Wednesday and Saturday nights.
Goal: fat loss while keeping muscle. I dislike chicken breast, broccoli, and yogurt.
I can buy beef, chicken thighs, rice, oats, potatoes, beans, tofu, eggs, milk, vegetables, and canned fish.
Create a one-week carb-cycling batch meal plan using raw weights and check fiber, potassium, sodium, calcium, magnesium, and Omega-3.
```

Then lock the shopping list to one store:

```text
Use $store-locked-grocery-planner.
Use the weekly meal plan above and lock the grocery order to Hema/Freshippo, using the Jinan Yinfeng Jiuxi City delivery area as the example.
Tell me the product names, package sizes, quantities, substitutions, and confidence so I can place an order.
```

## Example Output

Short excerpt:

| Date | Training | Carb Type | Calories | Protein | Carbs | Fat |
|---|---|---|---:|---:|---:|---:|
| Monday | Back + fasted cardio | Medium | 2425 | 174g | 284g | 68g |
| Wednesday | Arms + badminton | High | 2990 | 190g | 413g | 68g |
| Sunday | Rest / light cardio | Low | 2225 | 170g | 209g | 89g |

Store-locked grocery excerpt:

| Category | Product target | Pack size | Buy qty | Required | Confidence |
|---|---|---:|---:|---:|---|
| Chicken | Hema Daily Fresh boneless skinless chicken thigh / diced chicken thigh | 300g | 5 | 1290g | Medium, app verification needed |
| Milk | Hema organic skim milk / low-fat pure milk | 950ml | 5 | 4700ml | Medium |
| Fish can | Water-packed mackerel or tuna | 150-200g | 2 cans | 240g drained | Low until label verified |

See [`docs/examples.en.md`](docs/examples.en.md) for a fuller English walkthrough, or [`docs/examples.md`](docs/examples.md) for the Chinese version. The example includes calculations, calendar, rice-bean bases, recipe steps, per-serving nutrition, storage/reheating, daily pickup, and the Hema grocery list.

## Safety and Accuracy

These skills provide general nutrition and grocery-planning support, not medical advice. Plans involving kidney disease, diabetes medication, potassium restrictions, anticoagulants, pregnancy, eating-disorder history, severe allergy, or clinician-directed nutrient restrictions should be reviewed by a physician or registered dietitian.

The grocery skill does not invent live inventory. If a retailer hides store-specific inventory behind an app login, outputs must be labeled as candidates unless the user provides screenshots, links, or cart data.

## Repository Layout

```text
skills/
  carb-cycle-batch-meal-planner/
    SKILL.md
    agents/openai.yaml
  store-locked-grocery-planner/
    SKILL.md
    agents/openai.yaml
docs/
  examples.md
  examples.en.md
LICENSE
README.md
README.en.md
```

## License

Apache License 2.0. See [`LICENSE`](LICENSE).
