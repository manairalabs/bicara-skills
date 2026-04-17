---
name: invoice-extract-id
description: >
  Extract structured data from Indonesian invoices, receipts, and tax invoices (faktur pajak).
  Use when the user uploads a PDF or image of an Indonesian business document and needs
  vendor info, NPWP, line items, DPP, PPN, PPh, totals, payment terms, and bank details
  pulled into JSON for bookkeeping, reimbursement, or ERP import.
license: MIT
version: 0.1.0
---

# Invoice Extract — Indonesia

Use this skill when extracting structured data from Indonesian business documents:
receipts (kwitansi / nota), tax invoices (faktur pajak), vendor bills, purchase orders,
delivery orders, and bank transfer proofs.

## When to use (trigger phrases)

- "extract this nota / kwitansi / invoice / faktur"
- "read this faktur pajak"
- "bikin data akuntansi dari PDF ini"
- "ambil NPWP dan PPN dari dokumen"
- "convert invoice Indonesia to JSON"

## Output contract

Always produce JSON matching this shape. Use `null` for fields that are absent in the
source; never hallucinate values. Numbers must be integers in IDR (round to nearest
rupiah). Dates must be ISO 8601 (`YYYY-MM-DD`).

```json
{
  "documentType": "tax_invoice | invoice | receipt | purchase_order | delivery_order | bank_transfer",
  "documentNumber": "string | null",
  "issueDate": "YYYY-MM-DD | null",
  "dueDate": "YYYY-MM-DD | null",
  "vendor": {
    "name": "string | null",
    "npwp": "string | null",
    "nitku": "string | null",
    "address": "string | null",
    "phone": "string | null"
  },
  "buyer": {
    "name": "string | null",
    "npwp": "string | null",
    "address": "string | null"
  },
  "items": [
    {
      "description": "string",
      "quantity": "number | null",
      "unit": "string | null",
      "unitPrice": "number | null",
      "discount": "number | null",
      "subtotal": "number"
    }
  ],
  "dpp": "number | null",
  "ppn": {
    "rate": "number | null",
    "amount": "number | null"
  },
  "pph": {
    "code": "string | null",
    "rate": "number | null",
    "amount": "number | null"
  },
  "stampDuty": "number | null",
  "totalDue": "number",
  "amountInWords": "string | null",
  "payment": {
    "method": "transfer | cash | qris | card | null",
    "bankName": "string | null",
    "accountNumber": "string | null",
    "accountName": "string | null",
    "paidAt": "YYYY-MM-DD | null"
  },
  "notes": "string | null"
}
```

## Extraction rules

**NPWP normalization.** Accept both 15-digit legacy (`XX.XXX.XXX.X-XXX.XXX`) and
16-digit post-2024 formats. Strip dots, dashes, and whitespace. Validate digits only;
reject if count is not 15 or 16.

**PPN detection.** Indonesian statutory PPN: 11% through 2024, 12% from Jan 2025.
If the document date is known, prefer the rate in force at that date. If the invoice
shows explicit `PPN 11%` / `PPN 12%`, trust the document.

**PPh codes.** Common withholding codes to recognize:
- PPh 21 — employee income
- PPh 23 — services (2% or 15% depending on category)
- PPh 4(2) — rent / construction (final)
- PPh 22 — import / certain sales

**Faktur pajak rules.** A valid faktur pajak has a 16-digit serial
(`XXX.XXX-XX.XXXXXXXX`) and a QR code. If both are present, classify as `tax_invoice`.

**Amount consistency check.** After extraction, verify:
- `sum(items[].subtotal) ≈ dpp` (allow rounding of ±1 rupiah per line)
- `dpp × ppn.rate ≈ ppn.amount` (allow ±1 rupiah)
- `dpp + ppn.amount - pph.amount + stampDuty ≈ totalDue`

If any check fails, set `notes` to describe the discrepancy; do not "correct" the
numbers silently.

**Terbilang (amount in words).** Common on formal invoices. Capture as-is without
recomputing.

**Addresses.** Indonesian addresses can include `RT/RW`, `Kelurahan`, `Kecamatan`,
`Kota/Kabupaten`, province, and postal code. Preserve the original line breaks inside
the `address` string using `\n`.

**Handwritten receipts.** Many UMKM receipts are handwritten. Still fill required
fields; use `notes` to flag low-confidence values instead of omitting them.

**Bank transfer proofs.** Treat as `bank_transfer` type. `totalDue` is the transferred
amount. `payment.method = "transfer"`, `payment.paidAt` = transfer date.
`documentNumber` = transfer reference / trace ID if shown.

## Common pitfalls

- **Don't confuse buyer and vendor.** The NPWP with the word "Penjual" or "Pengusaha
  Kena Pajak" is the vendor. The buyer may not have an NPWP (UMKM / personal).
- **Don't invent line items.** Some receipts show only a total; leave `items` as
  `[]` rather than fabricating.
- **Don't parse thousand separators as decimals.** Indonesian locale: `.` is thousands,
  `,` is decimal. `Rp 1.500.000,50` is one-point-five million rupiah, fifty sen.
- **Don't treat `NPWP -` as a real NPWP.** Some templates leave placeholder dashes.
  Return `null` for absent NPWP.

## See also

- Indonesian locale utilities: [`@manairalabs/id-locale`](https://www.npmjs.com/package/@manairalabs/id-locale)
  covers NPWP validation/formatting, IDR parsing, and PPN/PPh calculation.
