# Meal Planning Codex Skills

中文 | [English](README.en.md)

这个仓库包含两个 Codex skills，用来把健身饮食需求整理成可以执行的一周系统：

- `carb-cycle-batch-meal-planner`：生成碳水循环一周食谱、集中备餐流程、储存复热方案和营养闭环校验。
- `store-locked-grocery-planner`：把食谱转换成锁定某个商超/门店/配送区域的下单清单，包括商品名、包装规格、购买数量、替代品和置信度。

推荐组合使用：先生成营养和备餐方案，再锁定到某个超市或外卖平台生成购物车清单。

## Skills

| Skill | 用途 |
|---|---|
| [`carb-cycle-batch-meal-planner`](skills/carb-cycle-batch-meal-planner/SKILL.md) | 根据身体数据、训练安排、饮食偏好、可购食材、厨具、储存条件和营养目标，生成一周碳水循环食谱。 |
| [`store-locked-grocery-planner`](skills/store-locked-grocery-planner/SKILL.md) | 将食谱或原料表转换为某个商超的下单清单，计算包装数量、余量、替代商品、实时库存限制和标签检查项。 |

## 安装

克隆仓库，然后把需要的 skill 文件夹复制到 Codex skills 目录。

PowerShell：

```powershell
git clone https://github.com/NTIITM/meal-planning-skills.git
Copy-Item -Recurse .\meal-planning-skills\skills\carb-cycle-batch-meal-planner "$env:USERPROFILE\.codex\skills\"
Copy-Item -Recurse .\meal-planning-skills\skills\store-locked-grocery-planner "$env:USERPROFILE\.codex\skills\"
```

Bash：

```bash
git clone https://github.com/NTIITM/meal-planning-skills.git
cp -R meal-planning-skills/skills/carb-cycle-batch-meal-planner ~/.codex/skills/
cp -R meal-planning-skills/skills/store-locked-grocery-planner ~/.codex/skills/
```

如果你设置了 `CODEX_HOME`，请复制到 `$CODEX_HOME/skills`。

## 快速使用

先使用碳循环备餐 skill：

```text
Use $carb-cycle-batch-meal-planner.
我24岁，男，182cm，88kg。每周训练6天，周三和周六晚上打羽毛球。
目标是减脂保肌。不喜欢鸡胸肉、西兰花和酸奶。
能买到牛肉、鸡腿肉、米饭、燕麦、土豆、豆类、豆腐、鸡蛋、牛奶、蔬菜和鱼罐头。
帮我做一周碳循环集中备餐计划，用生重/干重计算，并检查纤维、钾、钠、钙、镁和 Omega-3。
```

再把购物清单锁定到某个商超：

```text
Use $store-locked-grocery-planner.
根据上面的一周食谱，锁定到济南银丰玖玺城附近的家家悦超市。
请告诉我商品名、包装规格、购买数量、替代品和置信度，让我可以直接下单。
```

## 示例结果

食谱输出摘录：

| 日期 | 训练 | 碳水类型 | 热量 | 蛋白质 | 碳水 | 脂肪 |
|---|---|---|---:|---:|---:|---:|
| 周一 | 背+空腹有氧 | 中碳 | 2425 | 174g | 284g | 68g |
| 周三 | 手臂+羽毛球 | 高碳 | 2990 | 190g | 413g | 68g |
| 周日 | 休息/轻活动 | 低碳 | 2225 | 170g | 209g | 89g |

锁定商超购物清单摘录：

| 类别 | 商品目标 | 包装规格 | 购买数量 | 需要量 | 置信度 |
|---|---|---:|---:|---:|---|
| 鸡肉 | 原味去皮去骨鸡腿肉 | 300g | 5 | 1290g | 中，或 App 截图确认 |
| 牛奶 | 无糖低脂/脱脂纯牛奶 | 250ml x 24 | 1箱 | 4700ml | 中 |
| 鱼罐头 | 水浸青花鱼/鲭鱼/金枪鱼 | 150-200g | 2罐 | 沥干240g | 标签确认前为低 |

完整示例见 [`docs/examples.md`](docs/examples.md)。

## 安全与准确性

这些 skills 只提供一般营养、备餐和购物规划信息，不替代医疗建议。涉及肾病、糖尿病用药、钾限制、抗凝药物、妊娠或哺乳、饮食失调史、严重过敏、医生要求限制营养素等情况时，应由医生或注册营养师审核。

购物清单 skill 不会伪造实时库存。如果商超把门店库存放在 App 登录、定位或账号会话之后，输出必须标注为候选商品，除非用户提供截图、链接或购物车数据。

## 仓库结构

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
LICENSE
README.md
README.en.md
```

## 许可证

Apache License 2.0。见 [`LICENSE`](LICENSE)。
