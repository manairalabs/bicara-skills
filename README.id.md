# bicara-skills

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

**Paket Claude skill untuk operasional UKM Indonesia.** Kumpulan file `SKILL.md` yang mengajarkan Claude untuk menangani tugas bisnis Indonesia yang umum: ekstraksi invoice/nota, balasan customer service WhatsApp Bahasa Indonesia, dan lainnya seiring waktu.

*[English](README.md)*

## Isi paket

| Skill | Fungsi |
|-------|--------|
| [`invoice-extract-id`](skills/invoice-extract-id/SKILL.md) | Ekstrak data terstruktur dari invoice / nota / faktur pajak Indonesia ke JSON — lengkap dengan validasi NPWP, tarif PPN/PPh, terbilang, dan detail bank. |
| [`wa-reply-id`](skills/wa-reply-id/SKILL.md) | Draft balasan customer service WhatsApp dalam Bahasa Indonesia dengan register yang tepat untuk retail, F&B, dan jasa. Bukan terjemahan mesin dari Bahasa Inggris. |

Skill lain akan bertambah seiring waktu. Lihat [katalog di program OSS kami](https://github.com/manairalabs/.github) untuk rencana berikutnya.

## Cara pakai

### Dengan aplikasi Claude (Claude.ai)

1. Clone repo ini atau download `skills/<nama>/SKILL.md` yang dibutuhkan.
2. Ikuti panduan setup skill dari Anthropic untuk aplikasi Claude Anda.

### Dengan Claude Code

Letakkan folder skill di dalam `.claude/skills/` di project Anda:

```bash
mkdir -p .claude/skills
cp -r skills/invoice-extract-id .claude/skills/
```

### Dengan Paperclip, OpenClaw, atau runtime lain yang mendukung SKILL.md

Skill ini memakai format standar `SKILL.md` (frontmatter YAML + body markdown), kompatibel dengan runtime manapun yang membaca format tersebut.

## Kontribusi

Pull request terbuka. Prioritas saat ini:

- Skenario tambahan untuk `wa-reply-id` (vertikal khusus: ojek, properti, pendidikan)
- Skill pelengkap: `pph21-helper`, `spt-preview`, `stock-opname-id`
- Contoh faktur pajak nyata untuk test set skill ekstraksi

Lihat [CONTRIBUTING.md](CONTRIBUTING.md).

## Lisensi

MIT — lihat [LICENSE](LICENSE).

## Siapa yang merawat ini

[Manaira Labs](https://manairalabs.com). Kami membangun produk AI dan menyediakan konsultasi untuk bisnis Indonesia. Skill-skill ini diekstrak dari pemakaian produksi di [Bicara Business Platform](https://bicara.ai), platform native AI yang kami operasikan untuk UKM Indonesia.

Proyek open-source terkait:

- [`@manairalabs/id-locale`](https://github.com/manairalabs/id-locale) — utilitas locale Indonesia untuk TypeScript (IDR, NPWP, NIK, telepon, matematika PPN/PPh, terbilang).
