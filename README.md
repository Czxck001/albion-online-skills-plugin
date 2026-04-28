# Albion Online Plugin for Claude Code

A complete Albion Online assistant plugin for Claude Code with 6 specialized skills covering every major aspect of the game. Updated for the **Abyssal Depths patch series (2025)**.

## Install

```bash
/plugin install https://github.com/Czxck001/albion-online-skills-plugin
```

## Skills Included

| Skill | Invocation | What it does |
|-------|-----------|-------------|
| **Destiny Board Advisor** | `/albion-online:destiny-board-advisor` | Gear builds, weapon meta, Destiny Board progression paths |
| **Market Intelligence** | `/albion-online:market-intelligence` | Live prices via Albion Data Project API, arbitrage, silver/hr |
| **Crafting Calculator** | `/albion-online:crafting-calculator` | Crafting profitability, refining math, return rates, journal bonuses |
| **Content Planner** | `/albion-online:content-planner` | Activity guide: dungeons, The Depths, Hellgates, gathering, Mists |
| **Guild & Alliance Tools** | `/albion-online:guild-alliance-tools` | ZvZ/GvG strategy, 2v2 Hellgate comps, territory management, guild comms |
| **Lore & Onboarding** | `/albion-online:lore-onboarding` | New player guide, game systems, 2025 Orange PvP and The Depths explained |

Skills are also **auto-invoked** — Claude will load the relevant skill automatically when you ask Albion-related questions without needing to type the slash command.

## Usage Examples

```
What's a good solo PvP build for corrupted dungeons?
→ auto-invokes destiny-board-advisor

Where should I sell my T6 hide right now?
→ auto-invokes market-intelligence (fetches live prices)

Is it profitable to craft Bloodletters in Caerleon?
→ auto-invokes crafting-calculator

What should I be doing at T6 gear?
→ auto-invokes content-activity-planner

What's a good 2v2 Hellgate comp?
→ auto-invokes guild-alliance-tools

I just started playing, what do I do?
→ auto-invokes lore-onboarding
```

## What's Covered (Abyssal Depths 2025)

- ✅ Current weapon meta (Abyssal Depths Patch 5/6)
- ✅ The Depths — new Orange PvP dungeon (June 2025)
- ✅ 2v2 / 5v5 / 10v10 Hellgates with IP caps, lava mechanic, build breakdowns
- ✅ Recent balance changes (Polehammer buff, Mistwalker nerf, Lifetouch rework, etc.)
- ✅ Live market data via [Albion Online Data Project API](https://www.albion-online-data.com/)
- ✅ Reworked new player experience (Adventurer / Duelist / Gatherer paths)
- ✅ Learning Points daily delivery change
- ✅ Brecilien city bonus (Nature/Arcane Staffs)

## Plugin Structure

```
albion-online/
├── .claude-plugin/
│   └── plugin.json
└── skills/
    ├── destiny-board-advisor/SKILL.md
    ├── market-intelligence/SKILL.md
    ├── crafting-calculator/SKILL.md
    ├── content-planner/SKILL.md
    ├── guild-alliance-tools/SKILL.md
    └── lore-onboarding/SKILL.md
```

## Contributing

PRs welcome! If a patch drops and meta shifts, open an issue or submit a PR updating the relevant `SKILL.md`.

## License

MIT
