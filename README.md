# Product Design Tools

Claude Code skills for product design at Mosaic Wellness.

## Skills

| Skill | Description | Brands |
|-------|-------------|--------|
| [design-audit](skills/design-audit/) | UX, UI & Brand audit with 8-domain scoring and PDF scorecard | Little Joys, Man Matters, Be Bodywise |

## Quick Install

```bash
# Clone the repo
git clone https://github.com/rohitmudliyar-mw/product-design-tools.git

# Copy the skill you want into your Claude Code skills directory
cp -r product-design-tools/skills/design-audit ~/.claude/skills/design-audit
```

Then open Claude Code and use `/design-audit` or say "audit this design."

## Requirements

- [Claude Code](https://claude.ai/code) (CLI, desktop, or IDE extension)
- Google Chrome (for PDF generation)

## Adding New Skills

Each skill lives in its own folder under `skills/`. To add a new one:

1. Create `skills/your-skill-name/SKILL.md`
2. Add a `README.md` with usage instructions
3. Add any supporting files (templates, brand contexts, etc.)

Built at Mosaic Wellness. Powered by [Claude Code](https://claude.ai/code).
