# Examples

English | [中文](examples.md)

This document shows a combined workflow: first use `carb-cycle-batch-meal-planner` to generate a weekly carb-cycling meal-prep plan, then use `store-locked-grocery-planner` to turn it into a Hema/Freshippo grocery order.

## Example 1: Weekly Carb-Cycling Batch Meal Plan

User prompt:

```text
Use $carb-cycle-batch-meal-planner.
I am 24, male, 182cm, 88kg. I train six days per week: Monday back, Tuesday chest, Wednesday arms, Thursday shoulders, Friday chest, Saturday back.
I play badminton for about 90 minutes on Wednesday and Saturday nights and do 30 minutes of fasted cardio every morning.
Goal: fat loss while keeping muscle.
I dislike broccoli, chicken breast, and yogurt.
I want beans cooked together with rice, and all grocery quantities should use raw or dry weights.
I can buy beef, chicken thighs, rice, oats, potatoes, vegetables, tofu, eggs, milk, black beans, red beans, soybeans, chickpeas, and canned fish.
Create a one-week carb-cycling meal plan, batch-prep timeline, storage/reheating plan, and checks for fiber, Omega-3, potassium, sodium, calcium, and magnesium.
```

Calculation excerpt:

```text
BMR: about 1903 kcal
Estimated TDEE: about 3140 kcal
Weekly fat-loss target: about 2550-2600 kcal/day
Protein target: about 170-190g/day
High-carb days: Wednesday and Saturday
Medium-carb days: Monday, Tuesday, Thursday, Friday
Low-carb day: Sunday
```

### Weekly Calendar

| Day | Training | Carb Type | Calories | Protein | Carbs | Fat | Fiber |
|---|---|---|---:|---:|---:|---:|---:|
| Monday | Back + fasted cardio | Medium | 2425 | 174g | 284g | 68g | 36g |
| Tuesday | Chest + fasted cardio | Medium | 2510 | 187g | 288g | 77g | 37g |
| Wednesday | Arms + badminton | High | 2990 | 190g | 413g | 68g | 41g |
| Thursday | Shoulders + fasted cardio | Medium | 2510 | 163g | 315g | 70g | 38g |
| Friday | Chest + fasted cardio | Medium | 2500 | 186g | 283g | 77g | 39g |
| Saturday | Back + badminton | High | 2830 | 169g | 420g | 55g | 38g |
| Sunday | Rest / light activity | Low | 2225 | 170g | 209g | 89g | 38g |

### Rice-Bean Bases

Beans are weighed dry before soaking. Soak for `8-12 hours`. If using a normal rice cooker, black beans, soybeans, and chickpeas should be par-cooked before being cooked with rice. A pressure rice cooker can usually use the mixed-grain mode.

| Day | Lunch Rice-Bean Base | Dinner Rice-Bean Base |
|---|---|---|
| Monday | rice 70g + black beans 15g | rice 70g + chickpeas 15g |
| Tuesday | rice 70g + black beans 15g | rice 55g + soybeans 10g |
| Wednesday | rice 95g + red beans 20g, plus potatoes 250g | rice 105g + red beans 5g |
| Thursday | rice 55g + black beans 10g, plus potatoes 250g | rice 70g + chickpeas 15g |
| Friday | rice 70g + chickpeas 15g | rice 55g + soybeans 10g |
| Saturday | rice 110g + red beans 20g, plus potatoes 300g | rice 105g + red beans 5g |
| Sunday | rice 30g + black beans 10g | rice 30g + chickpeas 10g |

### Breakfast

| Day Type | Breakfast |
|---|---|
| Medium-carb | oats 70g + milk 500ml + 2 eggs + chia seeds 8g + blueberries 100g |
| High-carb | oats 85g + milk 500ml + 2 eggs + chia seeds 8g + banana 120g + blueberries 80g |
| Low-carb | oats 55g + milk 450ml + 2 eggs + chia seeds 8g + blueberries 80g |

### Core Batch Recipes

| Recipe Module | Raw / Dry Ingredients | Use | Storage |
|---|---|---|---|
| Tomato mushroom beef | lean beef 960g, tomatoes 1000g, mushrooms 480g, onion 200g, spinach 320g, olive oil 12g, low-sodium soy sauce 20g | Monday lunch, Wednesday lunch, Thursday dinner, Sunday dinner | Refrigerate first 3 days; freeze later boxes |
| Ginger garlic chicken thigh | boneless skinless chicken thigh 1290g, carrots 420g, red bell pepper 240g, bok choy 610g, olive oil 12g, low-sodium soy sauce 25g | Monday dinner, Tuesday lunch, Wednesday dinner, Friday lunch, Saturday dinner | Badminton pre-meal portions use less oil and fewer leafy vegetables |
| Tofu egg tomato | firm tofu 840g, eggs 3, tomatoes 600g, spinach 240g, mushrooms 300g, olive oil 6g, low-sodium soy sauce 15g | Tuesday dinner, Friday dinner, Sunday lunch | Best refrigerated for 2-3 days; freezing changes texture |
| Canned fish potato bowl | water-packed mackerel/salmon/tuna 2 cans, about 240g drained; potatoes 800g; tomatoes 300g; bok choy 200g | Thursday lunch, Saturday lunch | Open cans when eating; prep potatoes and vegetables ahead |

### Recipe List

#### Tomato Mushroom Beef

- Servings: 4.
- Ingredients: lean beef 960g, tomatoes 1000g, white mushrooms 480g, onion 200g, spinach 320g, olive oil 12g, low-sodium soy sauce 20g, ginger, garlic, and black pepper.
- Steps: Slice the beef and season with a little soy sauce, ginger, and garlic. Sear quickly with half the oil, then remove. Cook onion and mushrooms in the same pan, add tomatoes, and simmer until saucy. Return beef to the pan, fold in blanched spinach, and adjust seasoning.
- Estimated nutrition per serving: about 520 kcal, protein 57g, carbs 23g, fat 22g, fiber 6g, sodium about 420mg, potassium about 1450mg, calcium about 120mg, magnesium about 95mg, Omega-3 about 0.1g. Confidence: medium.
- Storage and reheating: Refrigerate Monday and Wednesday portions; freeze Thursday and Sunday portions. Move frozen boxes to the fridge the night before. Microwave 2-3 minutes, stirring once, until hot throughout.
- Substitutions: Use lean pork tenderloin or extra tofu instead of beef; use frozen spinach instead of fresh spinach. Regular soy sauce materially raises sodium and should be reduced.

#### Ginger Garlic Chicken Thigh

- Servings: 5.
- Ingredients: boneless skinless chicken thigh 1290g, carrots 420g, red bell pepper 240g, bok choy 610g, olive oil 12g, low-sodium soy sauce 25g, ginger, garlic, and white pepper.
- Steps: Cut chicken into chunks and marinate with ginger, garlic, soy sauce, and a little oil for 15 minutes. Cook at 180C in an air fryer or oven for 15-18 minutes, or pan-sear until cooked through. Stir-fry carrots and bell pepper until just tender; blanch or quick-stir-fry bok choy. Portion into 5 boxes. Wednesday and Saturday pre-badminton portions should use less oil and fewer leafy vegetables.
- Estimated nutrition per serving: about 475 kcal, protein 49g, carbs 13g, fat 23g, fiber 4g, sodium about 360mg, potassium about 950mg, calcium about 120mg, magnesium about 60mg, Omega-3 about 0.1g. Confidence: medium.
- Storage and reheating: Refrigerate first 3 days; freeze Friday and Saturday dinner portions. Move to the fridge the night before and reheat for 2-3 minutes in the microwave, or steam in a pan with a splash of water.
- Substitutions: Buy plain chicken thigh fillets and trim them yourself if needed. Avoid Orleans, black-pepper, or other marinated products unless sodium and sugar are recalculated.

#### Tofu Egg Tomato

- Servings: 3.
- Ingredients: firm tofu 840g, eggs 3, tomatoes 600g, spinach 240g, mushrooms 300g, olive oil 6g, low-sodium soy sauce 15g.
- Steps: Cut and drain tofu, then pan-sear until the surface sets. Scramble eggs into large curds and remove. Cook tomatoes and mushrooms until saucy, then add tofu, eggs, and spinach. Season and reduce briefly.
- Estimated nutrition per serving: about 415 kcal, protein 37g, carbs 23g, fat 21g, fiber 7g, sodium about 330mg, potassium about 1200mg, calcium about 650mg, magnesium about 150mg, Omega-3 about 0.1g. Confidence: medium.
- Storage and reheating: Best eaten within 2-3 refrigerated days. Freezing makes tofu firmer but still usable. Microwave 2 minutes, stir, then heat another 30-60 seconds.
- Substitutions: Use northern tofu, firm tofu, or pressed tofu. Do not use silken tofu for batch boxes because it releases more water and breaks easily.

#### Canned Fish Potato Bowl

- Servings: 2.
- Ingredients: 2 cans water-packed mackerel/chub mackerel/tuna, target drained weight about 240g; potatoes 800g; tomatoes 300g; bok choy 200g; black pepper, garlic powder, or a small amount of low-sodium soy sauce.
- Steps: Steam potato chunks and portion by weight. Blanch bok choy and pack tomatoes separately. Keep fish cans unopened until eating; open, drain, and add to the box after reheating potatoes and vegetables. If canned fish is high in sodium, skip extra soy sauce.
- Estimated nutrition per serving: about 550 kcal, protein 39g, carbs 75g, fat 10g, fiber 10g, sodium about 350-900mg, potassium about 1900mg, calcium about 160mg, magnesium about 110mg. Omega-3 depends on fish type; mackerel is usually higher than tuna. Confidence: medium to low, depending on the can label.
- Storage and reheating: Potatoes and vegetables can be refrigerated or frozen. Store cans at room temperature and open only before eating. Reheat potatoes and vegetables first, then add fish to avoid spreading fish odor.
- Substitutions: Prefer water-packed mackerel or chub mackerel, then water-packed tuna or canned salmon. Oil-packed cans can work, but fat and calories must be recalculated.

### Batch-Prep Timeline

| Time | Action |
|---|---|
| 00:00 | Drain soaked beans; start first rice-bean batch; steam potatoes |
| 00:10 | Cut and marinate chicken thighs; chop tomatoes, mushrooms, onion, carrots, bell pepper |
| 00:25 | Start chicken in air fryer/oven; start tomato mushroom beef on stove |
| 00:45 | Blanch spinach and bok choy; continue second/third rice-bean batches |
| 01:05 | Cook tofu egg tomato; portion breakfast oats and chia seed dry packs |
| 01:35 | Weigh rice-bean bases, protein dishes, and potatoes into meal boxes |
| 01:55 | Refrigerate Monday-Wednesday boxes; freeze Thursday-Sunday boxes; label everything |
| 02:10 | Clean work area and cookware |

### Daily Pickup Table

| Day | Breakfast | Lunch | Snack / Fruit | Dinner | Night-Before Action |
|---|---|---|---|---|---|
| Monday | medium-carb oats | beef + black bean rice | orange | chicken + chickpea rice | none |
| Tuesday | medium-carb oats | chicken + black bean rice | grapes + milk | tofu egg + soybean rice | none |
| Wednesday | high-carb oats | beef + red bean rice + potatoes | banana | low-oil chicken + low-bean red rice | none |
| Thursday | medium-carb oats | canned fish potato bowl + black bean rice | orange + milk | beef + chickpea rice | move frozen box to fridge Wednesday night |
| Friday | medium-carb oats | chicken + chickpea rice | apple + milk | tofu egg + soybean rice | move frozen box to fridge Thursday night |
| Saturday | high-carb oats | canned fish potato bowl + red bean rice | banana | low-oil chicken + low-bean red rice | move frozen box to fridge Friday night |
| Sunday | low-carb oats | tofu egg + black bean rice | apple + small nuts | beef + chickpea rice | move frozen box to fridge Saturday night |

### Nutrition Loop

| Item | Target | Plan Average | Status |
|---|---:|---:|---|
| Calories | 2550-2600 kcal/day | about 2570 | OK |
| Protein | 165-190g/day | about 177g | OK |
| Fiber | 35-40g/day | about 38g | OK |
| Sodium | preferably below 2300mg/day | about 1600mg before brand-label variation | Requires low-sodium soy sauce and lower-sodium fish cans |
| Potassium | >=3400mg/day | >6000mg | High; not suitable for kidney disease or potassium restriction |
| Calcium | >=1000mg/day | about 1900mg | OK |
| Magnesium | >=400mg/day | about 670mg | OK |
| Omega-3 | ALA plus fish EPA/DHA | covered by chia seeds and fish cans | OK |

## Example 2: Hema/Freshippo Store-Locked Grocery Order

User prompt:

```text
Use $store-locked-grocery-planner.
Use the weekly plan above and lock the grocery order to Hema/Freshippo, using the Jinan Yinfeng Jiuxi City delivery area as the example.
Give Hema-searchable product names or product targets, package sizes, buy quantities, required amounts, surplus, substitutions, and confidence.
```

Hema store inventory usually requires app login and location. The table below is an order-ready candidate list. If the user provides Hema app screenshots or cart exports, confidence can be raised to high.

| Category | Hema Product Name / Search Target | Pack Size | Buy Qty | Required | Surplus | Use | Confidence | Substitute |
|---|---|---:|---:|---:|---:|---|---|---|
| Chicken | Hema Daily Fresh boneless skinless chicken thigh / diced chicken thigh | 300g | 5 | 1290g | about 210g | chicken module | Medium, app verification needed | plain chicken thigh fillet; bone-in legs require 1.8-2kg |
| Beef | Hema Daily Fresh beef strips / tenderloin / round | 250g | 4 | 960g | about 40g | beef module | Medium, app verification needed | plain beef slices, not marinated |
| Eggs | Hema Daily Fresh eggs | 10-count | 2 | 17 eggs | 3 eggs | breakfast + tofu dish | Medium | any plain fresh eggs |
| Milk | Hema organic skim milk / low-fat pure milk | 950ml | 5 | 4700ml | about 50ml | breakfast and snack | Medium | 250ml x 24 low-fat/skim milk |
| Tofu | Hema Daily Fresh northern tofu / firm tofu | 300g | 3 | 840g | about 60g | tofu egg tomato | Medium | not silken tofu |
| Canned fish | water-packed mackerel / chub mackerel can | 150-200g | 2 | 240g drained | depends on drained weight | fish potato bowl | Low to Medium | water-packed tuna or canned salmon |
| Rice | Hema Wuchang rice / northeast rice | 1kg | 1 | 990g | about 10g | rice-bean bases | Medium | any plain rice |
| Black beans | black beans | 250-500g | 1 | 50g | large surplus | black bean rice | Medium | use next week |
| Red beans | adzuki beans / red beans | 250-500g | 1 | 50g | large surplus | red bean rice | Medium | no sweetened red beans |
| Chickpeas | chickpeas | 250-500g | 1 | 55g | large surplus | chickpea rice | Low to Medium | increase black beans, but flavor diversity drops |
| Soybeans | soybeans | 250-500g | 1 | 20g | large surplus | soybean rice | Medium | frozen edamame, but cooked-weight math changes |
| Oats | Hema high-fiber oats / plain oats | 700g | 1 | 505g | about 195g | breakfast | Medium | Quaker plain instant oats |
| Chia seeds | plain chia seeds | 100-200g | 1 | 56g | 44-144g | breakfast Omega-3/fiber | Low to Medium | flaxseed meal, recalculation needed |
| Tomatoes | tomatoes | 500g | 4 | 1900g | about 100g | beef, tofu, fish bowl | Medium | Provence tomatoes |
| Mushrooms | white mushrooms | 200g | 4 | 780g | about 20g | beef, tofu | Medium | shimeji mushrooms, different flavor |
| Spinach | spinach | 250g | 3 | 560g | about 190g | beef, tofu | Medium | frozen spinach |
| Bok choy | bok choy / Shanghai greens | 300g | 3 | 810g | about 90g | chicken, fish bowl | Medium | romaine/youmai greens, reheating texture differs |
| Carrots | carrots | 500g | 1 | 420g | about 80g | chicken module | Medium | none |
| Red bell pepper | red bell pepper | 2-3 pieces | 1 | 240g | depends on size | chicken module | Medium | yellow bell pepper |
| Onion | yellow onion | 2 pieces | 1 | 200g | about 100g | beef module | Medium | red onion |
| Potatoes | potatoes | 1kg | 1 | 800g | about 200g | high-carb fish bowls | Medium | mini pumpkin requires carb recalculation |
| Frozen blueberries | frozen blueberries | 500g | 2 | 640g | about 360g | breakfast | Medium | fresh blueberries, preferably bought twice |
| Bananas | bananas | 4-5 pieces | 1 | 480g | depends on size | high-carb days | Medium | apple/orange, training carbs differ |
| Oranges | oranges | 2 pieces | 1 | 400g | about 0 | snack | Medium | |
| Apples | apples | 2 pieces | 1 | 400g | about 0 | snack | Medium | |
| Grapes | grapes / red grapes small pack | 200-250g | 1 | 180g | 20-70g | early-week fruit | Medium | blueberries/oranges |
| Seasoning | Lee Kum Kee low-sodium soy sauce / low-salt soy sauce | 500ml | 1 | 60g | large surplus | sodium-controlled seasoning | Medium | regular soy sauce raises sodium |
| Oil | extra-virgin olive oil | 500-750ml | 1 | 30g | large surplus | light cooking | Medium | skip if already owned |

### Hema Order Timing

- Main order: meat, eggs, milk, tofu, rice, dry beans, oats, chia seeds, canned fish, roots/tubers, tomatoes, mushrooms, frozen blueberries.
- Wednesday top-up: leafy greens, bananas, grapes, and other fragile fruit/vegetables if needed.
- Freezing strategy: freeze later-week chicken and beef meal boxes; open fish cans only when eating; prefer frozen blueberries.

### Label Checks

| Product | Field to Check | Pass Condition |
|---|---|---|
| Canned fish | sodium, oil/water pack, drained weight | prefer water-packed/boiled and lower sodium |
| Milk | unsweetened status, fat level | low-fat or skim pure milk; no flavored breakfast milk |
| Oats | added sugar | plain oats |
| Chicken/beef | marinade status | plain raw meat, not black-pepper or Orleans marinated |
| Soy sauce | sodium | low-salt or low-sodium preferred |

## Notes for Chinese Grocery Platforms

For Hema/Freshippo, Jiajiayue, Meituan Maicai, JD Daojia, Ele.me, and similar platforms, SKUs and inventory are often gated by store, geolocation, and account session. `store-locked-grocery-planner` should produce an order-ready candidate list, but should not claim confirmed stock without app screenshots, cart exports, or official store-specific product pages.
