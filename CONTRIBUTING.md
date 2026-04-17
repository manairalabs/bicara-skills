# Contributing to bicara-skills

Thanks for wanting to help.

## What makes a skill a good fit for this repo

1. **Indonesia-specific.** This repo is the Indonesian SMB vertical. Generic skills belong elsewhere (there are plenty of general marketplaces).
2. **Reflects real operator practice.** Don't submit theoretical skills. The scenarios, tone, and output contracts should match what Indonesian businesses actually do.
3. **Self-contained.** A skill is one folder with a `SKILL.md`, an `examples/` dir, and nothing more. No external dependencies in the skill itself. If the skill advises using a library (e.g., `@manairalabs/id-locale`), link to it; don't bundle it.
4. **Safe to publish.** No customer data, no proprietary prompts from inside a SaaS, no PII in examples.

## File layout for a new skill

```
skills/<skill-name>/
├── SKILL.md
└── examples/
    ├── <scenario-1>.md
    └── <scenario-2>.md
```

`<skill-name>` is kebab-case. Suffix `-id` for skills that are Indonesia-specific (most are).

## SKILL.md shape

Use YAML frontmatter with at minimum:

```yaml
---
name: your-skill-name
description: >
  One to three sentences. Describe what the skill does, when to use it,
  and what shape the output takes. Written for Claude to understand, not for humans.
license: MIT
version: 0.1.0
---
```

Markdown body should have:

- A one-paragraph intro
- **When to use (trigger phrases)** — list of phrases a user would naturally say to invoke this skill
- **Output contract** or **Workflow** — what Claude should produce or do
- **Rules / pitfalls** — things to get right or avoid
- Optional: **See also** with links to related skills or libraries

Look at `skills/invoice-extract-id/SKILL.md` or `skills/wa-reply-id/SKILL.md` as references.

## Examples

Every skill must ship with at least one example in `examples/`. Format:

- Input: the realistic raw input Claude would see (customer message, document transcript, etc.)
- Expected output: what Claude should produce
- Notes: explain edge cases, tradeoffs, or why a particular choice was made

Examples are read by humans reviewing the skill AND are part of the contract. Keep them realistic and minimal.

## Pull request checklist

- [ ] Skill follows the file layout above
- [ ] `SKILL.md` has valid YAML frontmatter with `name`, `description`, `license`, `version`
- [ ] At least one example in `examples/`
- [ ] No PII, customer data, or proprietary prompts
- [ ] Skill added to the table in `README.md` and `README.id.md`
- [ ] `CHANGELOG.md` updated under `[Unreleased]`

## Reporting issues

Issues welcome for:

- Wrong or outdated tax rates / regulations referenced in skills
- Tone guidance that feels off for modern Indonesian business
- Scenarios that don't match common customer behavior
- Format bugs in frontmatter, JSON examples, etc.

## Code of conduct

Be respectful. This is a small project.

## Contact

Questions: [manairadm@gmail.com](mailto:manairadm@gmail.com).
