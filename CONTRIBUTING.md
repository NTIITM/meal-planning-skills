# Contributing

Contributions are welcome if they keep the skills practical, source-aware, and honest about uncertainty.

## Guidelines

- Keep `SKILL.md` concise enough for Codex to load efficiently.
- Do not add invented nutrition values, product names, prices, or live inventory claims.
- Prefer official food databases, retailer pages, product labels, or user-provided screenshots.
- Keep safety boundaries for medical, allergy, medication, and nutrient-restriction cases.
- When adding examples, make clear whether product availability is verified or only a candidate.

## Validation

If you have the Codex skill creator scripts installed, validate each skill folder:

```powershell
$env:PYTHONUTF8='1'
python "$env:USERPROFILE\.codex\skills\.system\skill-creator\scripts\quick_validate.py" ".\skills\carb-cycle-batch-meal-planner"
python "$env:USERPROFILE\.codex\skills\.system\skill-creator\scripts\quick_validate.py" ".\skills\store-locked-grocery-planner"
```

On Windows, use a Python executable that is not the Microsoft Store shim if `python` is not configured.
