# Example: Faktur Pajak (Standard Tax Invoice)

## Input (transcribed from a PDF faktur pajak)

```
FAKTUR PAJAK

Kode dan Nomor Seri Faktur Pajak: 010.000-25.12345678

Pengusaha Kena Pajak
Nama        : PT SUMBER MAKMUR SEJAHTERA
Alamat      : Jl. Industri Raya No. 45
              Kawasan Industri Cikarang
              Bekasi 17520
NPWP        : 01.234.567.8-901.234
NITKU       : 0000000000

Pembeli Barang Kena Pajak / Penerima Jasa Kena Pajak
Nama        : PT MITRA BOGA NUSANTARA
Alamat      : Jl. Merdeka No. 12, Jakarta Selatan 12190
NPWP        : 02.345.678.9-012.345

No.  Nama Barang / Jasa                Qty   Satuan   Harga Satuan     Jumlah Harga
1    Tepung Terigu Premium 25kg        100   sak      Rp    225.000    Rp  22.500.000
2    Gula Pasir Putih 50kg              20   karung   Rp    550.000    Rp  11.000.000
3    Minyak Goreng Curah 18L            50   jerigen  Rp    245.000    Rp  12.250.000

Harga Jual / Penggantian / DP / TP              : Rp  45.750.000
Dikurangi Potongan Harga                         : Rp           0
Dikurangi Uang Muka                              : Rp           0
Dasar Pengenaan Pajak                            : Rp  45.750.000
PPN = 12% x Dasar Pengenaan Pajak                : Rp   5.490.000

Terbilang: Lima puluh satu juta dua ratus empat puluh ribu rupiah

Jakarta, 15 Januari 2026
```

## Expected output

```json
{
  "documentType": "tax_invoice",
  "documentNumber": "010.000-25.12345678",
  "issueDate": "2026-01-15",
  "dueDate": null,
  "vendor": {
    "name": "PT SUMBER MAKMUR SEJAHTERA",
    "npwp": "012345678901234",
    "nitku": "0000000000",
    "address": "Jl. Industri Raya No. 45\nKawasan Industri Cikarang\nBekasi 17520",
    "phone": null
  },
  "buyer": {
    "name": "PT MITRA BOGA NUSANTARA",
    "npwp": "023456789012345",
    "address": "Jl. Merdeka No. 12, Jakarta Selatan 12190"
  },
  "items": [
    {
      "description": "Tepung Terigu Premium 25kg",
      "quantity": 100,
      "unit": "sak",
      "unitPrice": 225000,
      "discount": null,
      "subtotal": 22500000
    },
    {
      "description": "Gula Pasir Putih 50kg",
      "quantity": 20,
      "unit": "karung",
      "unitPrice": 550000,
      "discount": null,
      "subtotal": 11000000
    },
    {
      "description": "Minyak Goreng Curah 18L",
      "quantity": 50,
      "unit": "jerigen",
      "unitPrice": 245000,
      "discount": null,
      "subtotal": 12250000
    }
  ],
  "dpp": 45750000,
  "ppn": {
    "rate": 0.12,
    "amount": 5490000
  },
  "pph": {
    "code": null,
    "rate": null,
    "amount": null
  },
  "stampDuty": null,
  "totalDue": 51240000,
  "amountInWords": "Lima puluh satu juta dua ratus empat puluh ribu rupiah",
  "payment": {
    "method": null,
    "bankName": null,
    "accountNumber": null,
    "accountName": null,
    "paidAt": null
  },
  "notes": null
}
```

## Notes on this example

- NPWP normalized to digits-only (no dots or hyphens).
- DPP × 12% = 45,750,000 × 0.12 = 5,490,000 ✓ matches invoice PPN.
- DPP + PPN = 45,750,000 + 5,490,000 = 51,240,000 = totalDue ✓.
- Terbilang preserved verbatim from the document.
