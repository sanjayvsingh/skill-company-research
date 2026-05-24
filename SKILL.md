---
name: pm-company-research
description: PM-optimized company research skill for four use cases: (1) full-scope general research on a company, (2) interview preparation at a target company, (3) competitive analysis, (4) synthesizing a company's practices against industry patterns for strategic use. Use when the user says "research [company]" (triggers full research), "prepare for interview at [company]", "competitive analysis of [company]", "how does [company] approach [topic]", or "benchmark [company] against us". Generates structured markdown reports combining executive thinking, product strategy, PM organizational culture, Seven Powers competitive analysis, and market intelligence.
---

# PM Company Research

## Overview

A three-mode research framework built for product managers. Produces structured intelligence reports that combine executive philosophy, product strategy, PM organizational dynamics, Seven Powers competitive moat analysis, and market positioning — going beyond marketing copy to capture how a company actually thinks and operates.

**Research modes — determined from user context or stated explicitly:**
- **`interview`** — Deep company understanding for PM job interviews
- **`competitive`** — Product and market intelligence for competitive analysis
- **`strategy`** — Executive thinking and industry practices for strategic synthesis against your own company's knowledge base

If no mode is specified, or if the user's needs span multiple modes, run comprehensive (all sections).

---

## Research Workflow

### Step 1: Confirm Mode and Scope

Before starting, identify mode from context:
- "research [company]" with no other qualifier → `comprehensive` (all sections)
- User mentions interview, job application, or hiring → `interview`
- User mentions competitors, market, benchmark, or "vs." → `competitive`
- User mentions strategy, industry practices, or their own company context → `strategy`
- Ambiguous → default to `comprehensive`

Also note:
- If multiple companies: confirm the list, then research sequentially, completing one company fully before starting the next
- If a product URL is provided: treat that product as the primary focus for Sections 6 and 14

### Step 2: Research the Company

**Output files:** `[Company-Name].md` and `[Company-Name].html` in the current working directory (hyphens, no spaces)
**Examples:** `Figma.md` + `Figma.html`, `Linear.md` + `Linear.html`

**Screenshots folder:** `[Company-Name]-screenshots/` in the current working directory
- Save 3–5 product screenshots per company (see Screenshot Workflow below)
- Reference screenshots in the markdown and HTML with relative paths

**Source strategy — in priority order:**
1. Official pages: About, Careers, Product, Engineering Blog, Investor Relations, Press, Newsroom
2. Executive interviews: podcasts (Lenny's Podcast, Masters of Scale, How I Built This, All-In, acquired.fm, SaaStr), conference keynotes, earnings call transcripts, long-form press interviews
3. Reputable external press: TechCrunch, The Verge, Bloomberg, WSJ, Wired, The Information
4. PM intelligence: Glassdoor PM-specific reviews, Blind, LinkedIn PM job descriptions, PM interview forums
5. Product intelligence: app store listings, G2, Capterra, user reviews, product documentation, changelog
6. Analyst sources: Gartner, Forrester, Crunchbase, SEC filings, PitchBook

**Research depth by mode:**

| Mode | Primary sections | Tool calls |
|------|-----------------|------------|
| `interview` | 1–4, 9, 14–15, 16 | 8–12 |
| `competitive` | 5–6, 10–13, 14 | 10–15 |
| `strategy` | 4, 7–8, 14–15 | 10–15 |
| Comprehensive | All | 12–18 |

### Screenshot Workflow

For each company, find and save 3–5 representative product screenshots:

**Finding screenshots:**
1. Official product landing page (look for hero images, feature screenshots, demo images)
2. App store listings — Apple App Store and Google Play often have high-quality screenshots
3. Company press kit or media kit (usually at `/press`, `/media`, or `/brand`)
4. ProductHunt launch page (often has curated screenshots)
5. G2 or Capterra product profile (user-submitted screenshots)

**Saving screenshots:**
- Create folder: `[Company-Name]-screenshots/`
- Download images using PowerShell: `Invoke-WebRequest -Uri "[image_url]" -OutFile "[Company-Name]-screenshots/[descriptive-name].png"`
- Name files descriptively: `dashboard.png`, `mobile-app.png`, `onboarding.png`, `pricing.png`
- Reference in the markdown: `![Dashboard](./[Company-Name]-screenshots/dashboard.png)`

**Screenshot placement:** Add an inline Screenshots subsection within Section 5 (Products & Services) and/or Section 6 (Product Deep Dive), immediately after describing the relevant feature or product.

**If screenshots cannot be downloaded:** Note the source URLs in a "Screenshot Sources" list at the bottom of Section 6 so images can be viewed manually.

### HTML Report

After the markdown file is complete and screenshots are saved, write `[Company-Name].html` containing the same content, structured for browser viewing. The HTML file must be fully self-contained — all CSS embedded in a `<style>` block, no external stylesheets or fonts, so it works offline.

**Layout and structure:**
- Sticky left sidebar with a table of contents linking to each section by anchor ID
- Main content area to the right, with section headings matching the markdown structure
- Page title at the top with company name and date generated

**Images:**
- Display product screenshots inline using relative paths: `./[Company-Name]-screenshots/filename.png`
- Wrap images in a responsive grid (two columns on wide screens, one column on narrow)
- Include a caption under each image using the filename as fallback text
- If a screenshot could not be downloaded, show a placeholder box with the source URL as a link

**Seven Powers ratings:**
- Display each rating as a small colored badge next to the power name
- Strong: green background; Emerging: amber; Weak: orange; None: red; Unknown: light gray
- Keep badge text as a single word (Strong, Emerging, Weak, None, Unknown)

**Styling guidelines:**
- White background, dark gray body text (#222), system font stack (system-ui, sans-serif)
- Section headings in a dark accent color; sidebar in a light gray background (#f5f5f5)
- Responsive: sidebar collapses to a top navigation bar on narrow screens
- Tables styled with alternating row shading and a visible header row
- Blockquotes (used for executive quotes) styled with a left border and light background
- No decorative imagery, gradients, or non-semantic color

### Step 3: Product Deep Dive Document (Optional)

Create a separate file `[Product-Name]-Features-and-Functionality.md` when: user requests deeper product analysis, a specific product URL is provided, or Section 6 can't do the product justice.

---

## Document Structure

### Executive Summary *(always present — written last, placed first)*

Write this section after completing all other sections, then move it to the top of the document. Two paragraphs, no subsections, no bullets.

**Paragraph 1 — What the company is:** Describe the company in plain language: what it does, who it serves, how it makes money, and where it sits in the market. A reader with no prior knowledge of the company should finish this paragraph with a clear mental model of the business.

**Paragraph 2 — Why it matters for this research:** Synthesize the most important findings relative to the user's research mode. For `interview` mode: what defines this company's PM culture and what a strong candidate needs to know. For `competitive` mode: the company's core strategic position and where its moat is strongest or weakest. For `strategy` mode: the most transferable insight or the sharpest contrast with conventional industry practice. This paragraph should read like the one thing you'd say if you only had 30 seconds to brief someone.

---

### Section 1: Company Mission & Vision

- Official mission or vision statement — verbatim with source citation
- One-sentence plain-language interpretation
- How leadership talks about the mission in interviews (does it match the website?)
- If not publicly stated: note explicitly rather than inferring

### Section 2: Company Values & Culture

- Explicitly stated values with citations (source: About, Careers, annual reports)
- Cultural signals from engineering blog, job postings, and executive communication
- **PM-relevant cultural indicators:**
  - Is product framed as a strategic function or an execution function?
  - What language do they use about customers, data, and speed?
  - Any signals about psychological safety, failure tolerance, or debate culture?

### Section 3: Key Facts

5–7 concise, sourced facts. Include "As of [date]" on time-sensitive data.

- **Founded:** Year, founding story, original problem
- **Headquarters:** Location(s), remote posture
- **Scale:** Headcount range, revenue range or ARR, or funding raised
- **Leadership:** CEO, CPO, founders — note tenure and background
- **Business model:** How the company makes money (SaaS, marketplace, usage-based, etc.)
- **Milestones:** Notable product launches, acquisitions, pivots, or recognitions

### Section 4: Executive Insights *(PM-critical — all modes)*

This section captures how leadership actually thinks — not what the marketing site says.

**Sources to prioritize:** CEO/CPO/VP Product podcast appearances, conference talks, earnings call transcripts, long-form press interviews. Look for candid, unguarded statements.

For each key executive (CEO, CPO, Head of Product):

- **Name, title, tenure**
- **Product philosophy:** How do they talk about building product? What do they optimize for?
- **Key quotes:** 2–3 substantive statements with source + date (avoid PR copy)
- **Current strategic priorities:** What problems are they focused on right now?
- **Leadership style signals:** How do they talk about teams, failure, process, and speed?

**Quality bar:** A quote like "we put customers first" is not useful. Look for specifics: how they made a hard call, what they believe that others don't, how they think about trade-offs.

### Section 5: Products & Services

Catalog of the company's main offerings:
- **[Product Name]** — One-sentence description of what it does
- Mark the primary product (or URL-specified product) in **bold**
- Note platform availability (web, mobile, desktop, API)
- Distinguish: core products vs. legacy products vs. beta/experimental

**Product screenshots** — embed 1–2 screenshots of the primary product interface here. Reference using relative paths from the screenshots folder.

### Section 6: Product Deep Dive *(for primary product)*

**6.1 How It Works**
- Core workflow and user journey (how a new user gets value)
- Key features (5–8) with brief descriptions
- Technical architecture overview if relevant and public

**6.2 Problems It Solves**
- 3–5 primary user pain points addressed
- Evidence from reviews, stated positioning, or executive commentary

**6.3 Recent Updates**
- New features or launches with dates
- Version releases or major changes
- Publicly shared roadmap signals

**6.4 Integrations & Ecosystem**
- Key third-party integrations
- API availability and developer ecosystem
- Import/export capabilities

**6.5 Product Screenshots**
Embed any additional screenshots here (feature deep dives, mobile views, onboarding). If images could not be downloaded, list source URLs:

```
Screenshot sources:
- [Description](url)
- [Description](url)
```

### Section 7: Transformation & Innovation Strategy *(PM-critical — strategy + competitive modes)*

How is the company evolving its product and business? This section ages fast — note dates on all claims.

- **AI/ML integration:** Is AI being built in? What's the stated philosophy — AI-native, AI-assisted, or AI-averse?
- **Platform strategy:** Is the company expanding to a platform/ecosystem or staying focused?
- **Go-to-market evolution:** Any shifts in how they reach or expand customers (PLG → enterprise, bottom-up → top-down)?
- **Build vs. buy vs. partner:** Acquisition history and signals
- **Organizational evolution:** Reorgs, new leadership hires, public strategic pivots
- **Process maturity signals:** How do they talk about building — agile, continuous delivery, design process?

### Section 8: Product-Led Growth & Data Culture *(PM-critical — strategy + competitive modes)*

- **PLG motions:** Does the company use freemium, self-serve, viral loops, or usage-based expansion?
- **Data-driven signals:** Evidence of experimentation culture, A/B testing, metrics-driven decisions
- **Ship cadence:** How frequently do they release? What does their changelog show?
- **Public metrics philosophy:** How do they talk about measurement and success?
- **Engineering/product blog evidence:** Any posts on experimentation, data infrastructure, or product analytics?

### Section 9: PM Organization & Culture *(PM-critical — interview + strategy modes)*

PM culture varies enormously. This section helps calibrate whether a company treats PMs as strategists or executors, and what working there as a PM actually looks like.

- **PM seniority and influence:** Do PMs set strategy, own the roadmap, or execute against engineering and exec priorities?
- **PM career path:** APM program? Path from IC to leadership? Evidence of internal vs. external hiring for senior roles?
- **Team structure:** Squads, pods, functional teams, or matrix? Embedded vs. centralized design/engineering?
- **Decision-making model:** Who owns roadmap calls — PM, engineering, or exec? Evidence of PM autonomy?
- **Skills valued:** Technical depth, data fluency, design taste, customer proximity, business acumen? (Read job descriptions carefully)
- **PM sentiment:** What do current and former PMs say on Glassdoor and Blind? Look specifically for PM reviews, not just general company reviews.

Sources: Glassdoor PM-specific reviews, Blind, LinkedIn job descriptions for PM roles, PM interview prep communities, company career pages.

### Section 10: Industry & Market Position

- **Industry:** Primary sector and sub-sector (e.g., "B2B SaaS — Developer Tooling")
- **Market position:** How the company is positioned relative to the market — niche, challenger, leader, category creator
- **Target segment:** Company sizes, industries, geographies, and buyer personas
- **Market trends:** Key tailwinds and headwinds the company is navigating
- **Key competitors:** Named, with one-line positioning summary per competitor
- **Moat:** Defensible advantage — network effects, data, switching costs, brand, distribution?

### Section 11: Customers & Use Cases

- **Buyer vs. user:** Who signs the contract vs. who uses the product daily (critical for B2B)
- **Target audience:** B2B/B2C, industries, company sizes, geographic focus
- **Customer segments:** Different personas or buyer types
- **Notable customers:** Named clients or published case studies (if available)
- **Use cases:** How customers actually use the product — specific workflows
- **Customer sentiment:** Quotes from reviews, app stores, or testimonials with sources

### Section 12: Pricing Model

- Tier names with price points and included features
- Pricing structure: seat-based, usage-based, flat, or hybrid
- Annual vs. monthly options; discount signals
- Freemium or free trial availability
- Enterprise/custom options
- Pricing philosophy signals: "land and expand," usage-based growth, or high-ACV gated?
- Note if pricing is not publicly disclosed

### Section 13: Competitive Positioning *(primary for competitive mode — brief in all modes)*

**Competitive landscape table:**

| Dimension | [This Company] | Competitor A | Competitor B |
|-----------|----------------|--------------|--------------|
| Core product | | | |
| Target customer | | | |
| Key differentiator | | | |
| Pricing model | | | |
| AI/tech approach | | | |
| PLG motion | | | |

**Differentiation analysis:**
- Where does this company clearly win vs. alternatives?
- Where are they most vulnerable?
- What is their strategic bet that competitors aren't making?
- What would a customer switch away for?

### Section 14: Seven Powers Analysis *(PM-critical — all modes)*

Hamilton Helmer's Seven Powers framework identifies the seven sources of durable competitive advantage. For each power, assess whether the company's primary product holds it, is building toward it, or lacks it — and provide evidence.

**Rating scale:** `Strong` / `Emerging` / `Weak` / `None` / `Unknown`

---

#### 14.1 Scale Economies
*Per-unit costs decline as volume grows, enabling price advantages competitors can't match at smaller scale.*

- **Rating:**
- **Evidence:** Does the company benefit from cost structures that get better with scale? (Infrastructure, content, support, R&D amortization)
- **Barrier to challengers:** What volume would a competitor need to match their cost base?

#### 14.2 Network Effects
*Each additional user makes the product more valuable to all existing users.*

- **Rating:**
- **Evidence:** Is there a direct network effect (users ↔ users) or indirect (users ↔ developers/suppliers)? Does value meaningfully increase with user growth?
- **Barrier to challengers:** Can a smaller network offer comparable value, or does the incumbent's scale create a winner-take-most dynamic?

#### 14.3 Counter-Positioning
*The company uses a business model that incumbents cannot copy without damaging their own existing business.*

- **Rating:**
- **Evidence:** Is the company doing something structurally different from incumbents? What would it cost an incumbent to replicate it?
- **Barrier to challengers:** Is the company itself now vulnerable to a counter-positioned challenger?

#### 14.4 Switching Costs
*Customers face meaningful financial, operational, or psychological costs when switching to an alternative.*

- **Rating:**
- **Evidence:** Are there data lock-in, workflow integration, training costs, or long implementation timelines that trap customers?
- **Barrier to challengers:** How much more value would a competitor need to offer to justify a customer switching?

#### 14.5 Branding
*The company commands a price premium or preference for an objectively comparable offering based on accumulated reputation.*

- **Rating:**
- **Evidence:** Does the brand carry premium pricing power or preference independent of product specs? Any evidence of brand-driven selection over cheaper alternatives?
- **Barrier to challengers:** How many years of consistent delivery would a challenger need to build comparable brand equity?

#### 14.6 Cornered Resource
*The company has preferential access to a unique, scarce asset — IP, data, talent, distribution, or relationships — that competitors cannot easily replicate.*

- **Rating:**
- **Evidence:** Does the company own irreplaceable IP, a unique dataset, an exclusive distribution channel, or a concentrated cluster of rare talent?
- **Barrier to challengers:** Is the resource genuinely unavailable to others, or merely expensive to acquire?

#### 14.7 Process Power
*The company's embedded operational excellence and institutional knowledge produces better outcomes that competitors cannot replicate even by observation.*

- **Rating:**
- **Evidence:** Are there published signals of exceptional operational discipline — engineering velocity, design quality, support responsiveness — that consistently outperforms peers?
- **Barrier to challengers:** How long would it take a competitor to develop equivalent process maturity?

---

#### 14.8 Seven Powers Summary

**Strongest powers:** [List top 1–3 with brief rationale]

**Powers being built:** [What the company is investing in that could become a power]

**Vulnerabilities:** [Where the company lacks power and is exposed to competitive attack]

**Strategic implication:** [One-sentence synthesis of what the Seven Powers profile means for this company's long-term competitive position]

---

### Section 15: Strategic Signals *(primary for strategy mode — brief in all modes)*

**What can PMs and product orgs learn from this company?**

This section is explicitly for synthesis — connecting what this company does to broader industry patterns and your own company's strategic context.

- **Replicable practices:** What is this company doing in product development, PM culture, data culture, or go-to-market that represents a transferable best practice?
- **Industry-shaping moves:** Is this company defining a new pattern others will follow (e.g., PLG before it had a name, AI-native product design)?
- **Lessons from failures or pivots:** Any public mistakes, shutdowns, or admitted wrong turns — and what they signal about what doesn't work
- **Benchmark signals:** Any public KPIs, conversion rates, retention benchmarks, or growth rates useful for industry comparison
- **PM takeaways:** 3–5 specific strategic lessons a PM can bring back and apply or pressure-test against their own company's approach

Mark any inferred conclusions explicitly: *"Inferred from [source] — not stated directly."*

### Section 16: PM Interview Prep Insights *(primary for interview mode — brief in all modes)*

3–5 numbered, actionable insights for a PM interviewing at this company. Generic advice ("show passion for the product") is not acceptable — every insight must be grounded in specific evidence from this research.

**Format:**
1. **[Insight Title]**
   - Supporting evidence from research (cite section)
   - How to apply this in an interview answer, cover letter, or portfolio framing
   - Specific talking point or example to use

**Insight topics to draw from:**
- PM skills to emphasize based on Section 9 (PM org culture and values)
- Executive priorities to reference from Section 4
- Product knowledge to demonstrate from Section 6
- Seven Powers vocabulary to demonstrate strategic PM thinking (Section 14)
- Values alignment from Section 2
- Market awareness to show from Sections 10–11
- Strategic context from Section 7

### Section 17: Sources

Numbered list of every source cited in the document:

```
1. [Site Name | Page Title](url) — accessed [date]
2. [Site Name | Page Title](url) — accessed [date]
```

Include all cited sources. Do not include sources not cited in the document.

---

## Multi-Company Research

When the user provides multiple companies:
1. Confirm the list and mode before starting
2. Research one company fully before starting the next (including screenshots)
3. Create one `.md` file per company in the current working directory
4. Create one `[Company-Name]-screenshots/` folder per company
5. After all companies are complete, generate a **Comparative Summary** highlighting the most relevant differences for the user's mode:
   - `interview`: PM org culture, values alignment, product philosophy
   - `competitive`: differentiation, pricing, PLG motion, Seven Powers profiles
   - `strategy`: replicable practices, strategic bets, PM takeaways
   - All modes: Seven Powers comparison table across all researched companies

**Seven Powers comparison table (multi-company):**

| Power | [Company A] | [Company B] | [Company C] |
|-------|-------------|-------------|-------------|
| Scale Economies | | | |
| Network Effects | | | |
| Counter-Positioning | | | |
| Switching Costs | | | |
| Branding | | | |
| Cornered Resource | | | |
| Process Power | | | |

---

## Quality Standards

Before finalizing any document:
- All major sections have content — or explicitly note why information is unavailable
- Every factual claim is cited with source and date
- Executive quotes are substantive, not PR copy — look for candor and specificity
- Seven Powers ratings are backed by evidence, not assumed from company reputation
- PM org assessment is evidence-based (job postings, Glassdoor PM reviews, blog posts), not inferred from general company reputation
- Interview insights are specific to this company's research, not generic PM advice
- Inferred conclusions are marked clearly: *"Inferred — not stated directly"*
- Time-sensitive data (headcount, revenue, pricing) includes "As of [date]"
- Screenshots folder exists and images are referenced correctly with relative paths

**What this skill produces:**
- Executive perspective on product strategy and company direction
- PM-specific organizational and cultural intelligence
- Seven Powers competitive moat analysis for each product
- Product screenshots saved locally and embedded in the report
- Actionable interview preparation or competitive/strategic analysis grounded in evidence

**What this skill does not produce:**
- Financial valuation or investment analysis
- SWOT frameworks
- Summaries of marketing copy
- Analysis based on a single source or unverified claims

---

## Common Pitfalls

| Pitfall | Solution |
|---------|----------|
| Reading only marketing pages | Seek executive interviews, engineering blogs, and PM job postings |
| Missing PM org signals | Read PM-specific Glassdoor reviews, LinkedIn PM job descriptions, interview forums |
| Using outdated intelligence | Prioritize last 12–24 months; mark all time-sensitive data with date |
| Generic interview insights | Ground every insight in specific evidence from this company's research |
| Blending opinion with fact | State facts in sections 1–13; clearly mark inferences in sections 14–16 |
| Ignoring failure signals | Actively look for pivots, shutdowns, admitted mistakes, and negative reviews |
| Shallow Seven Powers analysis | Each power needs evidence — don't rate "Strong" based on reputation alone |
| Confusing correlation with power | A large user base is not automatically Network Effects — verify that value actually increases per new user |
| Low-quality screenshots | Prefer official press kit or app store screenshots over low-res blog images |
| Broken image paths | Use relative paths (`./[Company]-screenshots/file.png`), test that files exist before referencing |

---

## Reference Files

Consult for detailed guidance on source evaluation, citation standards, and handling missing information:

**`references/research-guidelines.md`**
