# Product Design Tools

Claude Code skills for product design at Mosaic Wellness.

## Skills

| Skill | Description | Brands |
|-------|-------------|--------|
| [design-audit](skills/design-audit/) | UX, UI & Brand audit with 8-domain scoring and PDF scorecard | Little Joys, Man Matters, Be Bodywise |

---

## How to Install (Step by Step)

### What you need before starting

1. **Claude Code** — Download from [claude.ai/code](https://claude.ai/code). Available as a desktop app (Mac/Windows), CLI, or VS Code extension.
2. **A Claude subscription** — Pro ($20/month) or Team ($30/month). Claude Code needs this to work.
3. **Google Chrome** — Most people already have this. Needed for PDF generation.

### Installation steps

**Step 1: Open Claude Code**

Open the Claude Code app on your computer. You'll see a text input where you can type messages.

**Step 2: Ask Claude to install the skill**

Type this message exactly:

```
Install the design audit skill from https://github.com/rohitmudliyar-mw/product-design-tools
```

Claude Code will clone the repo and copy the skill into the right place for you.

**If Claude Code doesn't do it automatically**, copy and paste this command into Claude Code (prefix with `!` to run it as a terminal command):

```
! git clone https://github.com/rohitmudliyar-mw/product-design-tools.git /tmp/pdt && cp -r /tmp/pdt/skills/design-audit ~/.claude/skills/design-audit && rm -rf /tmp/pdt && echo "Installed!"
```

**Step 3: Verify it works**

Type `/design-audit` in Claude Code. If the skill loads, you're done.

---

## How to Use

### Running an audit

1. Open **Claude Code**
2. Type `/design-audit`
3. **Drag and drop a mobile screenshot** into the chat (or paste a URL)
4. Tell it which brand: **Little Joys**, **Man Matters**, or **Be Bodywise**
5. Give it a screen name (e.g., "Shop Page", "PDP - Nutrimix")
6. Wait 10-15 seconds — it will generate a **2-page PDF scorecard**

### Important rules

- **Mobile screenshots only** — the tool will reject desktop screenshots and ask for the mobile version
- Take screenshots at **375px width** (standard iPhone size)
- **How to get a mobile screenshot on your computer**: Open Chrome → right-click the page → Inspect → click the phone icon at top-left → select "iPhone 12 Pro" → take a screenshot

### What you get

A 2-page PDF with:
- **Overall score** (1-5) with letter grade
- **Spider chart** showing all 8 domains visually
- **8 score cards** with one-line summaries
- **3 strengths** — what's working well
- **Top 5 findings** — prioritized issues with specific fixes

### Getting more detail

After the quick scan, you can ask for a deep dive:
```
deep dive on brand compliance and accessibility
```
This gives 3-4 detailed findings per domain with evidence and fixes.

---

## Requirements

- [Claude Code](https://claude.ai/code) (desktop app, CLI, or IDE extension)
- Claude subscription (Pro or Team)
- Google Chrome (for PDF export)

## Adding New Skills

Each skill lives in its own folder under `skills/`. To add a new one:

1. Create `skills/your-skill-name/SKILL.md`
2. Add a `README.md` with usage instructions
3. Add any supporting files (templates, brand contexts, etc.)

---

Built at Mosaic Wellness. Powered by [Claude Code](https://claude.ai/code).
