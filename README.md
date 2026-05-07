# AEO Brand Scan

> **Free Claude / Cursor / Codex / Gemini CLI skill that shows how AI search engines actually describe your brand vs competitors — in 30 seconds, without leaving your terminal.**

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Version](https://img.shields.io/badge/version-0.1.0-brightgreen.svg)](CHANGELOG.md)
[![Built by GenPicked](https://img.shields.io/badge/built%20by-GenPicked-7c3aed.svg)](https://genpicked.com)

If your customers ask **ChatGPT, Claude, or Perplexity** for the best [your category] — does your brand even show up? This skill tells you in 30 seconds.

---

## What it does

You give it your brand name, 1–3 competitors, and a category. It runs four probes across the AI engines your customers actually use:

1. **Blind discovery** — runs `"If I needed a [category] today, what are the top 3 I should consider?"` against **Claude Haiku 4.5** + **GPT-5-mini** in parallel. No brand mentioned. We measure organic recall.
2. **Direct brand probe** — `"What are the pros and cons of [your brand]?"` on both engines. Captures the *exact text* AI says about you (quotable, screenshot-worthy).
3. **Web-grounded probe** — Perplexity Sonar Pro on the category. Surfaces how many sources AI engines cite (count + unique domains).
4. **Recommendations** — three prioritized actions you can take this week, anchored in research stats.

It returns a markdown scorecard: visibility score 0–100, share of voice %, per-model mention table, the actual quotes, citation depth, and a CTA based on your result.

## Why this matters (AEO / GEO / AI Search Optimization)

**73% of brands running AEO have no way to connect AI citations to revenue** ([Discovered Labs, 2026](https://discoveredlabs.com/blog/aeo-performance-metrics-what-to-measure-and-how-to-track-ai-citations)). Most AEO tools are vanity dashboards.

This skill is built by [GenPicked](https://genpicked.com) — the only AEO platform that **triangulates organic recall, brand authority, and head-to-head Latin Square comparison**. The free skill ships dimensions 1 and 2; the [full battleground](https://genpicked.com/free-tools) adds Latin Square + longitudinal monitoring + the actual citation URLs.

**Use this skill when** you want to answer:

- "Does ChatGPT recommend my brand to potential customers?"
- "What does Claude actually say about my product?"
- "How am I doing in AI search vs my competitors?"
- "Which sources do AI engines cite for my category?"
- "Is my brand showing up in Perplexity answers?"

If any of those questions sound familiar, run the skill.

## Install

### Claude Code

```bash
claude plugin install github:WannabDad/aeo-brand-scan
```

Then in any Claude Code session, just say:

> *"Run an AEO scan for Acme Dental SaaS — competitors are BrightSmile and Crest Pro, category is dental practice management software"*

### Cursor / Codex CLI / Gemini CLI

The skill follows the [Anthropic Agent Skills](https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills) open standard, adopted by 32+ tools as of December 2025. To install in your tool:

1. Clone this repo: `git clone https://github.com/WannabDad/aeo-brand-scan.git`
2. Point your agent at the directory (most tools auto-detect `SKILL.md`)
3. Invoke with the same natural-language prompt as Claude

### Manual / standalone

The skill is just a shell script + an API. You can also call it directly:

```bash
git clone https://github.com/WannabDad/aeo-brand-scan.git
cd aeo-brand-scan
chmod +x skills/scan/scripts/scan.sh
./skills/scan/scripts/scan.sh "Your Brand" "Competitor 1,Competitor 2" "your category" "yourbrand.com" "comp1.com,comp2.com"
```

The trailing two arguments are **optional** — provide them to enable brand logo display via Clearbit.

### Repository structure

```text
aeo-brand-scan/
├── .claude-plugin/
│   └── plugin.json          # Anthropic plugin manifest
├── skills/
│   └── scan/
│       ├── SKILL.md         # Skill instructions for Claude
│       └── scripts/
│           └── scan.sh      # POSIX shell that curls the API
├── README.md
├── LICENSE
└── CHANGELOG.md
```

## Example output

When you run the skill, Claude renders something like this:

```markdown
![Acme Dental SaaS](https://logo.clearbit.com/acmedental.com)

## BrightSmile is mentioned 4× more than Acme Dental SaaS in dental practice management software queries.

| Engine | Mentioned? | List Position |
| --- | --- | --- |
| Claude Haiku 4.5 | ❌ No | — |
| ChatGPT (GPT-5-mini) | ✅ Yes | #3 |

**Competitors:**
- ![](https://logo.clearbit.com/brightsmile.com) **BrightSmile** — 4 mentions, avg position #1
- ![](https://logo.clearbit.com/crestpro.com) **Crest Pro** — 1 mention, position #3

### What ChatGPT actually says about you
> Acme Dental SaaS is a practice management tool primarily aimed at small dental
> offices. It offers scheduling, billing, and patient records but lacks the
> broader integrations of larger competitors.

### What Claude actually says about you
> I don't have specific information about Acme Dental SaaS in my training data.

**Citation depth:** Perplexity cited 7 sources from 4 unique domains for this category.

### Recommendations
- Brands with structured data show up 40% more often in AI Overviews — review your schema markup for product and pricing pages.
- YouTube mentions show the strongest correlation with AI visibility (~0.74) — invest in video content covering category buying questions.
- AI engines cite editorial sources over self-published content — pursue PR placements in publications that already rank for your category.

**Interpretation:** A score of 22/100 means your brand has limited AI visibility.
The industry benchmark for dental practice management software is approximately 52.

### 🔒 What this free scan is missing
🔒 The 7 actual URLs Perplexity cited — and which competitor authored which.
🔒 Negative-polarity probe — "What are the biggest complaints about this brand?"
🔒 Latin Square head-to-head: a 1-vs-1 forced comparison vs each competitor across 20 buying-decision questions.

**Trend:** AEO scores in dental practice management software shifted an average of 12% in the last 30 days. A snapshot today is already stale tomorrow.

> **BrightSmile outranks you 4×. See exactly which sources AI engines cite for them.**
> [Run the full battleground →](https://genpicked.com/free-tools?branch=competitive_intel)
```

## What you can NOT do with this free skill

We're upfront about the cliff — these are the things you'll need the [full GenPicked product](https://genpicked.com) for:

| Free skill | Paid GenPicked |
| --- | --- |
| One-shot snapshot | Continuous weekly monitoring + alerts when scores shift |
| 1 blind probe + 1 brand probe = 4 total model calls | 50 questions × 5 clusters × 4 models = 1,000 calls |
| Single brand only | Multi-brand portfolio + agency client roster |
| Citation count + domains only | **The actual URLs Perplexity / ChatGPT / Claude cite**, plus content excerpts |
| 3 generic recommendations | Full optimization roadmap + content briefs + citation reverse-engineering |
| Markdown response with watermark | White-label PDF reports for clients |

If you're an agency selling AEO to clients at $2–12K per audit, the white-label PDF + multi-brand dashboard is what you want. The free skill is the lead magnet.

## How it compares

| | This skill | HubSpot AEO Grader | Mangools AI Search Grader | Profound |
| --- | --- | --- | --- | --- |
| Free | ✅ | ✅ | ✅ (limited) | ❌ |
| Runs inside Claude / ChatGPT | ✅ | ❌ | ❌ | ❌ |
| Triangulates blind + brand + Latin Square | Free skill: 2/3 | 1/3 | 1/3 | 2/3 |
| Surfaces "what AI actually says about you" | ✅ | ❌ | ❌ | ✅ |
| Shows citation depth | ✅ (counts) | ✅ | ❌ | ✅ |
| Built specifically for agencies | ✅ | ❌ | ❌ | ❌ |

## Privacy & data

- Inputs (brand, competitors, category, optional domains) are sent to `api.genpicked.com` over HTTPS.
- They're processed by **Anthropic** (Claude Haiku), **Azure OpenAI** (GPT-5-mini), and **Perplexity** (Sonar Pro). All standard B2B SaaS subprocessors.
- **No account, no API key, no signup required.**
- IP addresses are SHA-256 hashed before any logging.
- Rate-limited: 5 scans per IP per 24 hours, 50 per source per hour, hard $50/day cost cap globally.
- Full privacy policy: [genpicked.com/privacy/aeo-brand-scan](https://genpicked.com/privacy/aeo-brand-scan)

## FAQ

**Q: Is this real or just templated output?**
A: 100% real. The skill calls live Claude Haiku 4.5, Azure GPT-5-mini, and Perplexity Sonar Pro APIs every time. Each run costs us about $0.019 in inference — we eat the cost as a free tool.

**Q: How accurate is it?**
A: Brand mention detection uses fuzzy matching that handles `CalvinKlein` ≈ `Calvin Klein`, `M&M` ≈ `MM`, etc. Position parsing handles numbered lists, dash-bulleted lists, bold-markdown lists. The methodology mirrors the production [GenPicked](https://genpicked.com) measurement pipeline that paying customers use.

**Q: Why don't you give us the URLs Perplexity cites?**
A: That's the most valuable signal in AEO — knowing which exact pages AI engines trust for your category. We surface the *count* in the free skill so you know it exists, and gate the URL list behind the [paid product](https://genpicked.com/free-tools). Honest paywall design, not crippleware.

**Q: Can I run this for multiple brands at once?**
A: Not in the free skill. One brand per scan. The paid product supports multi-brand portfolios + agency client rosters.

**Q: Does this work for ecommerce / SaaS / law firms / X?**
A: Yes — any category where customers might ask AI engines for recommendations. The more specific your category string, the better the results.

**Q: How is this different from just asking ChatGPT directly?**
A: Three things. (1) We hit Claude AND ChatGPT in parallel, so you see model disagreements. (2) We add Perplexity for web-grounded source citations. (3) We do deterministic mention/position scoring so you can compare results week over week, not just eyeball them.

**Q: What if the API is down?**
A: Each probe has graceful degradation — if Anthropic times out, you still get the GPT-5-mini result, just with a weaker scorecard. If Perplexity fails, you get zeros on citations. Never a 500.

**Q: Can I self-host this?**
A: The skill itself is open source (MIT). The API endpoint at `api.genpicked.com` is hosted by us. You could fork the API code and run your own — but you'd pay your own Anthropic/Azure/Perplexity costs.

## Roadmap

- **v0.1.0** (current) — Claude Skill + Cursor / Codex / Gemini support via shared spec
- **v0.2** — ChatGPT App in OpenAI's Apps Directory (in review)
- **v0.3** — Sentiment scoring (positive / negative / neutral per model)
- **v0.4** — Negative-polarity probe added to free tier
- **v0.5** — Multi-language support (Spanish, French, German)

## Contributing

This is GenPicked-maintained but we welcome PRs. Especially:

- New community marketplace listings
- Better install instructions for additional agents (Goose, Kiro, Continue, etc.)
- Bug reports with reproducible inputs

Open an issue or PR on [github.com/WannabDad/aeo-brand-scan](https://github.com/WannabDad/aeo-brand-scan).

## License

MIT — see [LICENSE](LICENSE).

## Built by

[**GenPicked**](https://genpicked.com) — the AEO platform agencies use to win in AI search. Try the [full battleground](https://genpicked.com/free-tools) for free.

---

### Keywords

answer engine optimization, AEO, generative engine optimization, GEO, AI search optimization, ChatGPT SEO, Claude SEO, Perplexity SEO, brand visibility AI, share of voice LLM, AI brand monitoring, AI citation tracking, AI search visibility, claude skill, claude code plugin, cursor skill, codex skill, gemini cli skill, anthropic agent skills, AI search ranking, LLM brand mentions
