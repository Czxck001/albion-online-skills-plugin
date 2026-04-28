# Install

This repository currently ships portable skills in `skills/`. Some tools install skills directly, while others install a plugin that bundles skills. Review the files before installing any third-party skill or plugin.

## Claude Chat / Claude Desktop

Claude Chat and the Claude Desktop chat surface install custom skills as ZIP files.

1. Create one ZIP per skill folder:

   ```bash
   rm -rf dist
   mkdir -p dist/tmp
   for skill in skills/*; do
     [ -d "$skill" ] || continue
     name="$(awk -F': *' '/^name:/ {print $2; exit}' "$skill/SKILL.md")"
     mkdir -p "dist/tmp/$name"
     cp -R "$skill"/. "dist/tmp/$name"/
     (cd dist/tmp && zip -qr "../${name}.zip" "$name")
   done
   rm -rf dist/tmp
   ```

2. Open Claude.
3. Go to `Settings` / `Customize` > `Skills`.
4. Upload each ZIP from `dist/`.
5. Enable the skills and test with an Albion Online prompt.

Anthropic's docs say a valid custom skill ZIP should contain the skill directory itself, with `SKILL.md` inside that directory.

## Claude Cowork

Claude Cowork installs plugins from the `Customize` menu in Claude Desktop and can upload custom plugin files. Each Cowork plugin can bundle skills, connectors, and sub-agents.

This repo is skills-only, so use one of these paths:

- Quick path: upload the individual skill ZIPs from the Claude Chat instructions under `Customize` > `Skills`.
- Plugin path: wrap this repo in a Claude plugin by adding a `.claude-plugin/plugin.json`, then ZIP the plugin folder and upload it in Cowork via `Customize` > `Browse plugins` / custom plugin upload.

Minimal Claude plugin manifest:

```json
{
  "name": "albion-online",
  "description": "Albion Online gameplay, market, crafting, guild, and onboarding skills.",
  "version": "1.0.0",
  "author": {
    "name": "Czxck001"
  }
}
```

Claude Code plugin skills are invoked as `/albion-online:skill-name` when installed as a plugin. Before packaging as a plugin, make sure each folder under `skills/` matches the `name` in its `SKILL.md`; for this repo, that means renaming `skills/content-planner` to `skills/content-activity-planner` or changing that skill's frontmatter name.

## Claude Code

Claude Code can discover skills directly from user or project folders:

```bash
git clone https://github.com/Czxck001/albion-online-skills-plugin.git
mkdir -p ~/.claude/skills
for skill in albion-online-skills-plugin/skills/*; do
  [ -d "$skill" ] || continue
  name="$(awk -F': *' '/^name:/ {print $2; exit}' "$skill/SKILL.md")"
  rm -rf "$HOME/.claude/skills/$name"
  mkdir -p "$HOME/.claude/skills/$name"
  cp -R "$skill"/. "$HOME/.claude/skills/$name"/
done
```

For a project-local install:

```bash
mkdir -p .claude/skills
for skill in /path/to/albion-online-skills-plugin/skills/*; do
  [ -d "$skill" ] || continue
  name="$(awk -F': *' '/^name:/ {print $2; exit}' "$skill/SKILL.md")"
  rm -rf ".claude/skills/$name"
  mkdir -p ".claude/skills/$name"
  cp -R "$skill"/. ".claude/skills/$name"/
done
```

Then restart Claude Code and ask:

```text
What Skills are available?
```

To distribute as a Claude Code plugin instead of loose skills, add `.claude-plugin/plugin.json`, keep the `skills/` directory at the plugin root, test with:

```bash
claude --plugin-dir /path/to/albion-online-skills-plugin
```

For marketplace install, publish the plugin through a Claude plugin marketplace, then users can run:

```text
/plugin marketplace add owner/repo
/plugin install albion-online@marketplace-name
```

## ChatGPT

ChatGPT supports custom skills in eligible workspaces. Install the skills directly:

1. Create the ZIP files using the Claude Chat command above.
2. In ChatGPT, open your profile menu and select `Skills`.
3. Select `New skill` > `Upload from your computer`.
4. Upload each `dist/*.zip` skill.

OpenAI notes that skills are currently product-specific and do not automatically sync across ChatGPT and Codex, even though they follow the Agent Skills open standard.

## Codex

Codex can use skills from local user, repository, admin, and system skill folders. To install this pack for your user:

```bash
git clone https://github.com/Czxck001/albion-online-skills-plugin.git
mkdir -p ~/.agents/skills
for skill in albion-online-skills-plugin/skills/*; do
  [ -d "$skill" ] || continue
  name="$(awk -F': *' '/^name:/ {print $2; exit}' "$skill/SKILL.md")"
  rm -rf "$HOME/.agents/skills/$name"
  mkdir -p "$HOME/.agents/skills/$name"
  cp -R "$skill"/. "$HOME/.agents/skills/$name"/
done
```

For a repository-local install:

```bash
mkdir -p .agents/skills
for skill in /path/to/albion-online-skills-plugin/skills/*; do
  [ -d "$skill" ] || continue
  name="$(awk -F': *' '/^name:/ {print $2; exit}' "$skill/SKILL.md")"
  rm -rf ".agents/skills/$name"
  mkdir -p ".agents/skills/$name"
  cp -R "$skill"/. ".agents/skills/$name"/
done
```

Codex can also install individual skills by URL with `$skill-installer`:

```text
$skill-installer install https://github.com/Czxck001/albion-online-skills-plugin/tree/main/skills/destiny-board-advisor
$skill-installer install https://github.com/Czxck001/albion-online-skills-plugin/tree/main/skills/market-intelligence
$skill-installer install https://github.com/Czxck001/albion-online-skills-plugin/tree/main/skills/crafting-calculator
$skill-installer install https://github.com/Czxck001/albion-online-skills-plugin/tree/main/skills/content-planner
$skill-installer install https://github.com/Czxck001/albion-online-skills-plugin/tree/main/skills/guild-alliance-tools
$skill-installer install https://github.com/Czxck001/albion-online-skills-plugin/tree/main/skills/lore-onboarding
```

Restart Codex if newly installed skills do not appear. In a Codex thread, type `$` and select the skill, or ask an Albion Online question and let Codex invoke the relevant skill automatically.

To distribute this pack as a Codex plugin, add `.codex-plugin/plugin.json`:

```json
{
  "name": "albion-online",
  "version": "1.0.0",
  "description": "Albion Online gameplay, market, crafting, guild, and onboarding skills.",
  "skills": "./skills/"
}
```

Then add it to a Codex plugin marketplace, such as `$REPO_ROOT/.agents/plugins/marketplace.json` for a repo marketplace or `~/.agents/plugins/marketplace.json` for a personal marketplace.
