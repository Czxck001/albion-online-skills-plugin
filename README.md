# Albion Online Agent Skills

A portable Albion Online skill pack with 6 specialized Agent Skills covering the major parts of the game. The skills use the open `SKILL.md` folder format, so they can be installed in skills-compatible tools such as Claude, ChatGPT, and Codex.

Updated for the **Radiant Wilds update (April 2026)**.

## Install

See [INSTALL.md](INSTALL.md) for setup instructions for Claude Chat/Desktop, Claude Cowork, Claude Code, ChatGPT, and Codex.

## Skills Included

| Skill | Direct invocation | What it does |
|-------|-------------------|-------------|
| **Destiny Board Advisor** | `destiny-board-advisor` | Gear builds, weapon meta, Destiny Board progression paths |
| **Market Intelligence** | `market-intelligence` | Live prices via Albion Data Project API, arbitrage, silver/hr |
| **Crafting Calculator** | `crafting-calculator` | Crafting profitability, refining math, return rates, journal bonuses |
| **Content Planner** | `content-activity-planner` | Activity guide: dungeons, The Depths, Hellgates, gathering, Mists |
| **Guild & Alliance Tools** | `guild-alliance-tools` | ZvZ/GvG strategy, 2v2 Hellgate comps, territory management, guild comms |
| **Lore & Onboarding** | `lore-onboarding` | New player guide, game systems, Orange PvP, The Depths, and 1v1 Arena explained |

When installed as a Claude plugin named `albion-online`, invoke skills with `/albion-online:skill-name`. When installed as Codex skills, invoke them from the skill picker with `$skill-name`. Skills may also be invoked automatically when your prompt matches their descriptions.

## Usage Examples

```text
What's a good solo PvP build for corrupted dungeons?
-> uses destiny-board-advisor

Where should I sell my T6 hide right now?
-> uses market-intelligence and fetches live prices

Is it profitable to craft Bloodletters in Caerleon?
-> uses crafting-calculator

What should I be doing at T6 gear?
-> uses content-activity-planner

What's a good 2v2 Hellgate comp?
-> uses guild-alliance-tools

I just started playing, what do I do?
-> uses lore-onboarding
```

## What's Covered

- Current weapon meta for the Radiant Wilds update
- The Depths and Orange PvP
- 1v1 Arena and the Antiquarian's Den
- 2v2 / 5v5 / 10v10 Hellgates with IP caps, lava mechanic, and build breakdowns
- Live market data via [Albion Online Data Project API](https://www.albion-online-data.com/)
- Reworked new player experience
- Learning Points, Premium, island, zone, and progression systems
- Guild, alliance, ZvZ, GvG, and territory planning workflows

## Skill Structure

```text
albion-online-skills-plugin/
├── README.md
└── skills/
    ├── destiny-board-advisor/SKILL.md
    ├── market-intelligence/SKILL.md
    ├── crafting-calculator/SKILL.md
    ├── content-planner/SKILL.md
    ├── guild-alliance-tools/SKILL.md
    └── lore-onboarding/SKILL.md
```

## References

- [Agent Skills open standard](https://agentskills.io/)
- [Claude custom skills](https://claude.com/docs/skills/how-to)
- [Claude Code plugins](https://code.claude.com/docs/en/plugins)
- [Claude Cowork plugins](https://support.claude.com/en/articles/13837440-use-plugins-in-cowork)
- [ChatGPT skills](https://help.openai.com/en/articles/20001066-skills-in-chatgpt)
- [Codex Agent Skills](https://developers.openai.com/codex/skills)
- [Codex plugins](https://developers.openai.com/codex/plugins)

## Contributing

PRs welcome. If a patch drops and meta shifts, open an issue or submit a PR updating the relevant `SKILL.md`.

## License

MIT
