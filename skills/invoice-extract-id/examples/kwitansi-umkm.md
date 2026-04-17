# Example: Handwritten UMKM Receipt (Kwitansi)

## Input (transcribed from a handwritten kwitansi)

```
KWITANSI No: 045/KW/2026

Sudah terima dari : Ibu Sari
Uang sejumlah     : Tiga juta lima ratus ribu rupiah
Untuk pembayaran  : Pembelian kain batik pesanan
                    (10 potong @ Rp 350.000)

Rp 3.500.000,-

Jakarta, 12 Februari 2026

Hormat saya,
Toko Batik Mekar Jaya
Jl. Tanah Abang Blok A No. 15
(tanda tangan)
```

## Expected output

```json
{
  "documentType": "receipt",
  "documentNumber": "045/KW/2026",
  "issueDate": "2026-02-12",
  "dueDate": null,
  "vendor": {
    "name": "Toko Batik Mekar Jaya",
    "npwp": null,
    "nitku": null,
    "address": "Jl. Tanah Abang Blok A No. 15",
    "phone": null
  },
  "buyer": {
    "name": "Ibu Sari",
    "npwp": null,
    "address": null
  },
  "items": [
    {
      "description": "Pembelian kain batik pesanan",
      "quantity": 10,
      "unit": "potong",
      "unitPrice": 350000,
      "discount": null,
      "subtotal": 3500000
    }
  ],
  "dpp": null,
  "ppn": {
    "rate": null,
    "amount": null
  },
  "pph": {
    "code": null,
    "rate": null,
    "amount": null
  },
  "stampDuty": null,
  "totalDue": 3500000,
  "amountInWords": "Tiga juta lima ratus ribu rupiah",
  "payment": {
    "method": null,
    "bankName": null,
    "accountNumber": null,
    "accountName": null,
    "paidAt": null
  },
  "notes": "Handwritten kwitansi with no NPWP — UMKM receipt. No PPN applied."
}
```

## Notes on this example

- UMKM receipts often lack NPWP on both sides — leave `null`, do not invent.
- No PPN reported; `ppn.amount` stays `null`. The total is the raw agreed price.
- `items` can be reconstructed from the description line's `(10 potong @ Rp 350.000)` parenthetical.
- `notes` flags the document context for downstream accounting systems.
