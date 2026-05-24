# pm-company-research

A Claude Code skill for product managers that produces structured company intelligence reports. Combines deep product research, executive insights, PM organizational analysis, and Hamilton Helmer's **Seven Powers** competitive moat framework.

See [Inspiration](#inspiration) below for the two skills that informed early thinking on this one.

## Use Cases

This skill is optimized for three PM-specific research contexts:

| Mode | Trigger | Output focus |
|------|---------|-------------|
| **Full research** | "research [company]" | All 17 sections, all modes combined |
| **Strategy synthesis** | "how does [company] approach [topic]" | Executive thinking, PLG patterns, transferable practices |
| **Competitive analysis** | "competitive analysis of [company]" | Product differentiation, pricing, Seven Powers moat profile |
| **Interview prep** | "research [company] for interview" | PM org culture, executive philosophy, values alignment, talking points |

Mode is detected automatically from context. You can also state it explicitly.

## What's in a Report

Each research run produces a `[Company-Name].md` file in the current working directory and a `[Company-Name]-screenshots/` folder with saved product images.

The report always opens with an executive summary (written after all research is complete, placed at the top), followed by 17 sections:

1. Company Mission and Vision
2. Company Values and Culture
3. Key Facts
4. Executive Insights - leadership quotes, product philosophy, strategic priorities
5. Products and Services - with embedded screenshots
6. Product Deep Dive - features, workflows, integrations, recent updates
7. Transformation and Innovation Strategy - AI approach, platform direction, GTM shifts
8. Product-Led Growth and Data Culture - PLG motions, experimentation signals
9. PM Organization and Culture - seniority, autonomy, decision-making, career path
10. Industry and Market Position
11. Customers and Use Cases
12. Pricing Model
13. Competitive Positioning - comparison table vs. key competitors
14. **Seven Powers Analysis** - moat assessment across all 7 powers
15. Strategic Signals - transferable practices and industry benchmarks
16. PM Interview Prep Insights - grounded, company-specific talking points
17. Sources

### Seven Powers Analysis

Section 14 rates each of Helmer's seven powers (`Strong / Emerging / Weak / None / Unknown`) with evidence:

- **Scale Economies** - cost structure advantages that compound with volume
- **Network Effects** - value increases as the user base grows
- **Counter-Positioning** - business model incumbents can't copy without self-harm
- **Switching Costs** - data lock-in, workflow integration, training sunk costs
- **Branding** - price premium or preference independent of product specs
- **Cornered Resource** - unique IP, data, talent, or distribution access
- **Process Power** - embedded operational excellence competitors can't replicate

For multi-company runs, a cross-company Seven Powers comparison table is generated automatically.

## Installation

Clone this repository directly into your Claude Code skills directory:

```bash
# macOS / Linux
git clone https://github.com/sanjayvsingh/skill-company-research.git \
  ~/.claude/skills/pm-company-research

# Windows (Command Prompt)
git clone https://github.com/sanjayvsingh/skill-company-research.git "%USERPROFILE%\.claude\skills\pm-company-research"
```

Claude Code will detect the skill automatically on next launch. Confirm it's active by typing `/skills` in a Claude Code session. You should see `pm-company-research` listed.

### Updating

```bash
cd ~/.claude/skills/pm-company-research && git pull
```

## Usage

Trigger the skill naturally. Claude detects the intent and selects the right mode:

```
Research Figma
```
```
How does Figma approach product-led growth?
```
```
Competitive analysis of Linear vs. Jira vs. Asana
```
```
Research Notion for an upcoming PM interview
```
```
Research Stripe and Adyen using pm-company-research
```

You can also invoke it explicitly:

```
Research [company] using pm-company-research
```

## Output

```
[working directory]/
├── Figma.md                        ← full research report
├── Figma-screenshots/
│   ├── editor.png
│   ├── components.png
│   └── pricing.png
└── Linear.md                       ← if multiple companies requested
    Linear-screenshots/
    └── ...
```

## Inspiration

Two existing skills informed early thinking on this one and are worth knowing about:

- **[priankr/claude-skill-company-research](https://github.com/priankr/claude-skill-company-research)** - a well-structured general-purpose company research skill with strong source discipline and job seeker focus
- **[deanpeters/Product-Manager-Skills](https://github.com/deanpeters/Product-Manager-Skills/blob/main/skills/company-research/SKILL.md)** - a PM-oriented research framework emphasizing executive quotes, product philosophy, and organizational dynamics

This skill was designed from the ground up around a product manager's specific needs: interview prep, competitive analysis, and strategy synthesis. It adds the Seven Powers moat framework, PM org culture assessment, executive insight extraction, and product screenshot capture as core components.

The Seven Powers framework is from Hamilton Helmer's book [*7 Powers: The Foundations of Business Strategy*](https://7powers.com/).
