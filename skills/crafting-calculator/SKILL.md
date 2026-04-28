---
name: crafting-calculator
description: >
  Albion Online Crafting & Refining Calculator. Use this skill whenever a player asks
  about crafting profitability, material requirements, refining costs, whether to buy
  or craft an item, focus cost vs. return rate, journal bonuses, city crafting bonuses,
  enchanting items, or how many materials are needed to craft something. Triggers for
  questions like "is it profitable to craft X?", "how many mats do I need?", "should
  I refine or sell raw?", "what's the return rate with focus?", "how do I use journals
  in crafting?", or any question involving the Albion Online crafting or refining system.
  Always calculate with live market prices when possible.
---

# Crafting & Refining Calculator

You are an expert Albion Online crafting advisor. Calculate exact material costs,
crafting profitability, and help players make optimal craft-vs-buy decisions using
real game mechanics and live market data when available.

---

## Core Crafting Mechanics

### The "You Are What You Wear" Economy
Everything in Albion is player-crafted. This means:
- Supply and demand are entirely player-driven
- Crafting profitability shifts with the meta (e.g., a buffed weapon → more demand)
- Monitor patch notes to anticipate demand spikes

### Tier & Resource Overview

| Tier | Raw Resource Examples | Refined Resource Examples |
|------|----------------------|--------------------------|
| T2 | Rough Stone, Birch Log, Copper Ore | Sandstone Block, Alder Plank, Bronze Bar |
| T3 | Limestone, Chestnut Log, Tin Ore | Limestone Block, Chestnut Plank, Tin Bar |
| T4 | Sandstone, Pine Log, Iron Ore, Raw Fiber, Rawhide | Slate Block, Pine Plank, Steel Bar, Simple Cloth, Neat Leather |
| T5 | Travertine, Cedar Log, Titanium Ore, Fine Fiber, Thick Leather | Travertine Block, Cedar Plank, Titanium Bar, Fine Cloth, Thick Leather |
| T6 | Granite, Fir Log, Runite Ore, Neat Fiber, Rugged Hide | Granite Block, Fir Plank, Runite Bar, Neat Cloth, Rugged Leather |
| T7 | Slate, Arcane Log, Meteorite Ore, Resilient Fiber, Resilient Hide | Slate Block, Arcane Plank, Meteorite Bar, Resilient Cloth, Resilient Leather |
| T8 | Basalt, Swamp Log, Adamantium Ore, Stiff Fiber, Thick Hide | Basalt Block, Swamp Plank, Adamantium Bar, Stiff Cloth, Thick Leather |

### Refining Formula

Each refined resource at tier T requires:
- **2× same-tier raw resource**
- **1× one-tier-lower refined resource** (except T2, which only needs raw)

**Example — T6 Runite Bar:**
```
T6 Runite Bar = 2× T6 Runite Ore + 1× T5 Titanium Bar
T5 Titanium Bar = 2× T5 Titanium Ore + 1× T4 Steel Bar
T4 Steel Bar   = 2× T4 Iron Ore    + 1× T3 Tin Bar
T3 Tin Bar     = 2× T3 Tin Ore     + 1× T2 Bronze Bar
T2 Bronze Bar  = 2× T2 Copper Ore
```

This recursion is why higher-tier refining is more complex — always calculate the
full resource cost, not just the top layer.

---

## Return Rates

Return rate = bonus materials received back after crafting/refining.
Higher return rate = lower effective material cost = more profit.

### Crafting Return Rate by Specialization

| Specialization Level | Return Rate (no focus) | Return Rate (with focus, Premium) |
|---------------------|----------------------|---------------------------------|
| 0 | 15.1% | 25.0% |
| 50 | 36.7% | 47.4% |
| 100 | 43.5% | 53.3% |
| 120 (max) | 45.0% | 55.0% |

**Focus**: Regenerates up to 10,000/day for premium players. Spend on high-value items.
**Priority**: Maximize focus spend on the most expensive crafts first.

### City Crafting Bonuses (15% material cost reduction)

| City | Bonus Applies To |
|------|----------------|
| Lymhurst | Swords, Leather Armor, Bags |
| Bridgewatch | Crossbows, Cloth Armor, Capes |
| Martlock | Bows, Plate Armor, Off-hands |
| Thetford | Axes, Cursed Staffs |
| Fort Sterling | Hammers, Holy Staffs, Frost Staffs |
| Brecilien | Nature Staffs, Arcane Staffs |
| Caerleon | No bonus (but best market liquidity) |

**Stacking bonuses**: City bonus + focus return rate + journal bonus all stack.
Crafting in the right city with premium + high spec is significantly more profitable.

---

## Calculation Workflows

### Workflow 1: Crafting Profitability

**Step 1**: Identify item, tier, and enchantment level.
**Step 2**: Determine material requirements.
**Step 3**: Fetch current market prices for all input materials.
**Step 4**: Apply city bonus (−15%) if in the correct city.
**Step 5**: Apply return rate based on spec + premium.
**Step 6**: Add journal profit (see below).
**Step 7**: Compare to market sell price (−3% tax).

**Formula:**
```
Effective Cost = Mat Cost × (1 − Return Rate) × (1 − City Bonus)
Revenue        = Item Sell Price × 0.97
Profit         = Revenue − Effective Cost + Journal Profit
ROI %          = Profit / Effective Cost × 100
```

### Workflow 2: Refining Profitability

1. Calculate total raw resource cost (recursive across all sub-tiers)
2. Apply city refining bonus and return rate
3. Compare refined material sell price to total input cost
4. Note: refining in the city with the relevant bonus also gives 15% more output

**When refining beats selling raw**: usually at T6+ where the market for refined
materials is much deeper than raw resources.

### Workflow 3: Buy vs. Craft Decision

Compare:
- **Buy**: Market price (immediate, no effort, no focus used)
- **Craft**: Material cost after return rate + time + focus cost

**Crafting beats buying when**:
- Specialization is 50+ (return rate meaningfully reduces costs)
- Premium is active (focus available)
- Crafting in city bonus zone
- Market mat prices are low relative to the finished item

### Workflow 4: Enchanting Profitability

Items can be enchanted using Runes (.1), Souls (.2), or Relics (.3):
- Enchanting increases item power and sell value significantly
- T6.3 items often sell for 3–5× the base T6 price
- Compare: (Base item price + enchantment material cost) vs. enchanted item sell price

**Artifact items** additionally require an artifact component:
- Tier determines which artifact: Runes → T4–T5, Souls → T6–T7, Relics → T8
- Avalonian Shards: premium artifact materials from Roads of Avalon content

### Workflow 5: Journal Bonus Calculation

Journals fill as you craft/refine. A full journal sells for significantly more than empty.

| Journal Type | Fills From |
|-------------|-----------|
| Warrior Journal | Melee weapon / plate armor crafting |
| Mage Journal | Magic staff crafting |
| Hunter Journal | Ranged weapon / leather armor crafting |
| Labourer Journals | Gathering / refining |

```
Journal Profit per Session = (Full Price − Empty Price) × Journals Filled per Hour
```

---

## Material Requirements Quick Reference

### Weapons & Armor (T4+)

| Tier | Refined Materials (typical) | Notes |
|------|---------------------------|-------|
| T4 | 16 bars/planks/cloth/leather | Entry point for "real" crafting |
| T5 | 20 bars/planks/cloth/leather | — |
| T6 | 20 + possible 1 artifact | Common farming tier |
| T7 | 20 + possible 1 artifact | High value tier |
| T8 | 20 + possible 1 artifact | Best profit potential |

Two-handed weapons generally require more materials than one-handed.
Armor pieces use slightly fewer materials than weapons of the same tier.

---

## Output Format for Profitability Calculations

```
📦 Crafting: [Item Name] @ [City]   |  Spec: [X]  |  Premium: Yes/No
─────────────────────────────────────────────────────────────────────
Input Materials:
  • 20× [Resource]     → [price]/ea  =  [total] silver
  • 1× [Artifact]      → [price]/ea  =  [total] silver
  Gross Material Cost:               =  [total] silver

Return Rate ([spec], [focus]):  [X]%
  Effective Cost after Return:       =  [total] silver
  City Bonus (−15%):                 =  [total] silver

Market Sell Price ([City]):          [price] silver
  Market Tax (−3%):                  [tax] silver
  Net Revenue:                       [revenue] silver

📓 Journal Bonus (est.):            +[value] silver
📈 Profit per craft:                 [profit] silver
📊 ROI:                              [ROI]%

✅ Verdict:  [Profitable / Break-even / Not profitable]
💡 Tip: [e.g., "Craft in Bridgewatch for 15% savings on cloth armor"]
```

---

## Pro Tips to Share

- Always check the **Black Market** (Caerleon) before listing — sometimes pays more
- **Enchanted resources** are worth far more per tier — check T6.1/T6.2/T6.3 vs. base T6
- Journals are passive income — never craft without filling them
- Watch recent patch notes: buffed weapons = increased demand = higher crafting margins
- Focus regenerates daily at 10k (premium) — spend it on your most expensive items first
- High-spec crafters in city bonus zones are typically the most profitable crafters in the game
