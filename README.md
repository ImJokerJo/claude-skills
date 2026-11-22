# Claude Skills — Desmond's setup

Skills I use with Claude, plus a quick guide so you can copy my setup.

## Skills in this repo

| Skill | What it does | Author |
|---|---|---|
| [`deckless-study-kit`](skills/deckless-study-kit/SKILL.md) | Turns lecture slides + past papers into a complete **Learn Notes** page and a separate **Active Recall** page, so you can study without opening the slides. | Desmond |
| [`dribbble-ui-skills`](skills/dribbble-ui-skills/SKILL.md) | Dribbble-style UI constraints (light mode, Inter, 4px grid) for building interfaces. | design-skills (MIT), via MCP Market |

## Set up Claude like mine

### 1. Install these skills
**claude.ai / desktop app**
1. Download a skill folder (e.g. `skills/deckless-study-kit/`) and zip it so the zip contains the folder with `SKILL.md` inside.
2. claude.ai → **Settings → Capabilities → Skills → Upload skill** → choose the zip.
3. Toggle it on.

**Claude Code**
```bash
git clone https://github.com/ImJokerJo/claude-skills.git
mkdir -p ~/.claude/skills
cp -r claude-skills/skills/* ~/.claude/skills/
```

### 2. Turn on the built-in Anthropic skills
These come with Claude, so they're not copied here. Enable them in **Settings → Capabilities**:
- **Documents:** docx, pdf, pptx, xlsx
- **Design:** canvas-design, theme-factory, frontend-design, web-artifacts-builder
- **Productivity:** deep-research, skill-creator, morning brief, import-memory
- **Computer/browser:** Claude in Chrome, computer use (desktop app)

The open-source versions are at [anthropics/skills](https://github.com/anthropics/skills).

### 3. Connectors I use
Google Drive, Google Calendar, GitHub (Settings → Connectors).

## Using a skill
Ask in plain language, e.g. *"Make a deckless study kit for KQC7017, slides are in my Masters folder"*, or run it as a slash command: `/deckless-study-kit`.

## Contributing
Fork, add a folder under `skills/<name>/SKILL.md`, and open a PR.
