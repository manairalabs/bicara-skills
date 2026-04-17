# bicara-skills

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

**Claude skills for Indonesian SMB operations.** A curated pack of `SKILL.md` files that teach Claude how to handle common Indonesian business tasks: invoice/receipt extraction, Bahasa Indonesia customer service replies, and more as they ship.

*[Bahasa Indonesia](README.id.md)*

## What's in the pack

| Skill | What it does |
|-------|--------------|
| [`invoice-extract-id`](skills/invoice-extract-id/SKILL.md) | Extract structured data from Indonesian invoices, receipts, and tax invoices (faktur pajak) into JSON — with NPWP validation, PPN/PPh rates, terbilang, bank details. |
| [`wa-reply-id`](skills/wa-reply-id/SKILL.md) | Draft Bahasa Indonesia WhatsApp customer service replies in the right register for retail, F&B, and services. No machine-translated English. |

More skills will ship here over time. See the [catalog in the OSS program](https://github.com/manairalabs/.github) for what's planned.

## How to use these skills

### With Claude apps (Claude.ai)

1. Clone this repo or download the specific `skills/<name>/SKILL.md` you want.
2. Follow Anthropic's skill setup guide for your Claude app (desktop / web).

### With Claude Code

Drop the skill folder into your project's `.claude/skills/` directory:

```bash
mkdir -p .claude/skills
cp -r skills/invoice-extract-id .claude/skills/
```

Claude Code will discover `.skill.md` / `SKILL.md` files under that path.

### With Paperclip, OpenClaw, or any SKILL.md-compatible runtime

These skills use the standard `SKILL.md` format (YAML frontmatter + markdown body) and are compatible with any runtime that reads that format.

## Contributing

Pull requests welcome. Priorities right now:

- More scenarios for `wa-reply-id` (specific verticals: ojek, property, education)
- Companion skills: `pph21-helper`, `spt-preview`, `stock-opname-id`
- Real-world faktur pajak examples for the extraction skill's test set

See [CONTRIBUTING.md](CONTRIBUTING.md).

## License

MIT — see [LICENSE](LICENSE).

## Who maintains this

[Manaira Labs](https://manairalabs.com). We build AI products and consulting for Indonesian businesses. These skills are extracted from production use inside [Bicara Business Platform](https://bicara.ai), the AI-native platform we operate for Indonesian SMBs.

Related open-source work:

- [`@manairalabs/id-locale`](https://github.com/manairalabs/id-locale) — Indonesian locale utilities for TypeScript (IDR, NPWP, NIK, phone, PPN/PPh math, terbilang).
