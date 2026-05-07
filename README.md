# AEO Brand Scan

Free Claude / Cursor / Codex CLI / Gemini CLI skill that shows how AI search engines describe your brand compared to competitors. Built by [GenPicked](https://genpicked.com).

## Install (Claude Code)

```bash
claude plugin install github:WannabDad/aeo-brand-scan
```

(Will migrate to `genpicked/aeo-brand-scan` once the org is set up.)

## Usage

In Claude, just say:

> "Run an AEO scan for Acme Dental SaaS vs BrightSmile and Crest Pro in the dental practice management software space."

The skill will:

1. Run a blind discovery prompt and a brand probe across Claude Haiku 4.5 + GPT-5-mini.
2. Run a Perplexity-grounded probe and surface citation depth (count + unique domains).
3. Score visibility, share of voice, and per-model mention.
4. Hand back a markdown report with a CTA to the full battleground.

## Privacy

Scan inputs (brand, competitors, category) are sent to api.genpicked.com over HTTPS and processed by Anthropic, Azure OpenAI, and Perplexity APIs. No account is required. IP addresses are hashed before logging. See [genpicked.com/legal/aeo-brand-scan-privacy](https://genpicked.com/legal/aeo-brand-scan-privacy).

## License

MIT
