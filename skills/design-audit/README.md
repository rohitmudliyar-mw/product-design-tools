# Design Audit Skill

A Claude Code skill that performs structured UX, UI & Brand audits with scoring across 8 domains. Built for Mosaic Wellness brands (Little Joys, Man Matters, Be Bodywise).

Upload a mobile screenshot, get a PDF scorecard with spider chart, scores, strengths, and prioritized findings.

## What it does

1. You share a **mobile screenshot** (or URL)
2. The skill scores it across **8 domains** (1-5 scale, weighted per brand)
3. Outputs a **2-page PDF** with spider chart, score cards, strengths, and top 5 findings
4. Optionally **deep dive** into specific domains for detailed analysis

### The 8 Scoring Domains

| Domain | What it measures |
|--------|-----------------|
| Usability & Flow | Task completion, navigation, forms, feedback |
| Visual Design & Craft | Hierarchy, typography, color, spacing, consistency |
| Brand Compliance | Logo, colors, fonts, imagery, overall brand feel |
| Content & Communication | Clarity, microcopy, voice, errors |
| Accessibility | WCAG AA contrast, touch targets, focus states |
| Trust & Credibility | Social proof, transparency, certifications |
| Conversion Design | CTA clarity, friction, value proposition |
| Emotional Design | First impression, delight, tone, cognitive load |

Each domain is weighted differently per brand based on what matters most for that audience.

## Sample Output

The PDF scorecard includes:
- Overall score (e.g., 3.2 / 5.0 — Grade B)
- Spider chart visualizing all 8 domains
- 8 score cards with summaries and progress bars
- "What's Working Well" section (3 strengths)
- Top 5 findings with severity tags (P1/P2) and specific fixes

## Supported Brands

| Brand | Status | Key Focus |
|-------|--------|-----------|
| **Little Joys** | Complete | Children's nutrition. Trust-heavy (parents buying for kids). Warm, playful, organic aesthetic. |
| **Man Matters** | Complete | Men's health. Discretion-first. Science-backed, non-judgmental. Electric Blue brand. |
| **Be Bodywise** | Placeholder | Women's health. Empathy-driven. Needs brand context filled in. |

## Installation

### Requirements
- [Claude Code](https://claude.ai/code) (CLI, desktop app, or IDE extension)
- Google Chrome (for PDF generation via headless mode)

### Setup

1. Clone this repo:
   ```bash
   git clone https://github.com/rohitmudliyar-mw/product-design-tools.git
   ```

2. Copy the skill into your Claude Code skills directory:
   ```bash
   cp -r design-audit-skill ~/.claude/skills/design-audit
   ```

3. Done. Open Claude Code and the skill is ready to use.

### Alternative: Direct clone into skills
```bash
git clone https://github.com/rohitmudliyar-mw/product-design-tools.git ~/.claude/skills/design-audit
```

## Usage

### Quick Scan (default)
```
/design-audit
```
Then share a mobile screenshot. The skill will:
- Ask for brand (if not obvious) and screen name
- Reject desktop screenshots (mobile-first rule)
- Score all 8 domains
- Generate a 2-page PDF scorecard

### Deep Dive
After a quick scan, ask for more detail on specific domains:
```
deep dive on brand compliance and accessibility
```

### Example
```
User: /design-audit [uploads mobile screenshot]
Skill: What screen is this? (e.g., "Shop Page", "PDP - Nutrimix")
User: Shop page
Skill: [runs audit, generates PDF]
       Overall: 3.2 / 5.0 — Grade B
       PDF saved at audit-shop-page-2026-04-13.pdf
```

## Architecture

```
design-audit/
├── SKILL.md              # Core audit engine — scoring framework, rules, PDF generation
├── README.md             # This file
├── brands/
│   ├── littlejoys.md     # Full brand context: colors, typography, spacing, components,
│   │                     # personas, design principles, audit rules
│   ├── manmatters.md     # Full brand context: Athena design system tokens, typography,
│   │                     # buttons, icons, illustrations, personas, accessibility
│   └── bebodywise.md     # Placeholder — needs brand context
└── templates/
    └── spider-chart.html # HTML template for the PDF scorecard with canvas-based
                          # radar chart, score cards, strengths, and findings
```

### How it works

1. **SKILL.md** defines the audit framework: 8 domains, scoring rubric (1-5), output format, PDF generation steps, and cross-platform Chrome detection
2. **Brand files** contain everything the AI needs to ground its audit: exact hex colors, typography specs, component rules, personas, tone of voice, and brand-specific audit considerations
3. **Spider chart template** is a self-contained HTML file with inline CSS and Canvas JS that renders the radar chart, score cards, strengths, and findings — designed to fit exactly 2 pages when printed to PDF
4. **Chrome headless** converts the HTML to PDF. Falls back to saving HTML if Chrome isn't found.

### Scoring

Each brand defines its own domain weights. For example:

| Domain | Little Joys | Man Matters |
|--------|-------------|-------------|
| Trust & Credibility | 20% | 20% |
| Usability & Flow | 20% | 20% |
| Brand Compliance | 15% | 10% |
| Visual Design | 15% | 15% |
| Content | 10% | 10% |
| Accessibility | 10% | 10% |
| Conversion | 5% | 10% |
| Emotional Design | 5% | 5% |

Overall score = weighted average. Letter grades: A (4.5+), A- (4.0), B+ (3.5), B (3.0), C+ (2.5), C (2.0), D (1.5), F (<1.5).

## Adding a New Brand

1. Create `brands/yourbrand.md` following the structure of `littlejoys.md` or `manmatters.md`
2. Include: brand overview, domain weights, tone of voice, colors (with hex), typography, spacing, components, personas, and audit considerations
3. The skill will automatically detect the new brand file

## PDF Output

- Exactly **2 pages**: page 1 has the header, score, spider chart, and 8 score cards; page 2 has strengths, findings, and footer
- All sections use `break-inside: avoid` to prevent mid-element page breaks
- Cross-platform Chrome detection: macOS, Linux, Windows
- Falls back to HTML if Chrome isn't installed

## Rules

- **Mobile-first**: Desktop screenshots are rejected by default. 95% of users are on mobile.
- **Specific over generic**: Every finding references actual elements from the screenshot.
- **Honest scoring**: 3/5 means "meets basic expectations." Scores are not inflated.
- **Actionable fixes**: Every finding includes a specific recommendation.
- **Brand-grounded**: Findings connect to the brand's colors, typography, personas, and values.

## Built by

Built at Mosaic Wellness for the product design team.

Powered by [Claude Code](https://claude.ai/code).
