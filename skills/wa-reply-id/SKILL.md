---
name: wa-reply-id
description: >
  Draft Bahasa Indonesia WhatsApp customer service replies in the right tone for
  retail, F&B, and services businesses. Use when a customer sends a WhatsApp
  message (inquiry, complaint, order status, promotion question) and the operator
  needs a polite, appropriate reply in Bahasa — not machine-translated English.
license: MIT
version: 0.1.0
---

# WhatsApp Reply — Indonesia

Draft Bahasa Indonesia customer-service replies that sound like a competent human
operator wrote them: polite, brief, with the right register for the audience. Tuned
for Indonesian retail, F&B, and services businesses that talk to customers via
WhatsApp Business API or personal WhatsApp.

## When to use (trigger phrases)

- "bikin balasan WA untuk customer ini"
- "draft a WhatsApp reply in Bahasa"
- "customer complaining about order — how to reply"
- "polite rejection in Bahasa for this request"
- "respond to price inquiry in Indonesian"

## Tone register

Pick one of three registers based on signals. When unsure, default to **Formal-Friendly**.

### Formal-Friendly (default)

Use when: first contact, older customer, B2B, formal greeting from customer, complaint
handling, quotation follow-up.

Style:
- Address as "Kak" (unisex), "Ibu" / "Bapak" (if name is known)
- Opening: "Halo Kak [Nama], terima kasih sudah menghubungi [Brand]."
- Full sentences; no caps lock; 1–2 emoji max, at end of line
- Closing: "Silakan kalau ada yang ingin ditanyakan lagi" / "Terima kasih atas kesabarannya"
- Sign-off: "Salam, [Nama CS] / Tim [Brand]"

### Casual-Warm

Use when: repeat customer, younger demographic signals (slang in their message like
"dong", "sih", "btw"), friendly banter already established.

Style:
- Address as "Kak" or first name
- Opening: "Halo Kak! Siaapp 🙌"
- Contractions ok ("makasih", "udah", "gak")
- Emoji more freely (still max 2 per message)
- No forced sign-off

### Strictly-Formal

Use when: B2B procurement, official complaint letter, legal/warranty claim, government
or enterprise.

Style:
- "Yth. Bapak/Ibu [Nama]"
- No emoji
- Full formal spelling ("tidak" not "gak", "saya" not "aku")
- Structured: greeting — acknowledgment — response — next step — sign-off

## Response patterns by scenario

### 1. Price inquiry

Avoid dumping a price list. Acknowledge → give price OR ask qualifier → offer next step.

Template:
```
Halo Kak, terima kasih sudah bertanya 🙏
Untuk [produk/jasa], harganya [harga] ([kondisi jika ada]).
Mau saya bantu buatkan pesanannya?
```

If the price depends on variables:
```
Halo Kak! Harga kami tergantung [variabel: ukuran/jumlah/lokasi/dll].
Boleh minta info: [2–3 pertanyaan kualifikasi]?
Biar saya bantu hitungkan yang paling pas.
```

### 2. Stock / availability inquiry

Check first, then confirm with timing.

Template (available):
```
Halo Kak, untuk [produk] stok masih ada ya.
Kalau mau order sekarang, besok/lusa bisa dikirim.
```

Template (out of stock):
```
Halo Kak, mohon maaf untuk [produk] sedang habis stok.
Perkiraan restock sekitar [tanggal].
Boleh saya kabari Kakak kalau sudah ready lagi?
```

### 3. Order status / shipping

Give the update first, then context. Customers want the answer, not the story.

Template:
```
Halo Kak, pesanan Kakak nomor [##] statusnya [status].
[Resi: ####### / Estimasi sampai: tanggal / Kendala: ###].
Ada yang ingin saya bantu lagi?
```

### 4. Complaint

Acknowledge → empathize → take ownership → resolve or escalate → close with care.

**Do not** ask the customer to repeat information they've already given.
**Do not** blame couriers/suppliers/etc. without owning the brand side.

Template (product defect):
```
Halo Kak, mohon maaf sekali pesanannya mengalami [masalah] 🙏
Ini tidak seharusnya terjadi. Untuk solusinya, kami bisa [penukaran / refund / perbaikan].
Mana yang paling pas untuk Kakak?
Terima kasih sudah bersabar, dan sekali lagi kami minta maaf atas ketidaknyamanannya.
```

### 5. Refund / cancellation

Confirm the request → state the policy simply → give the timeline → close.

Template:
```
Halo Kak, baik. Untuk refund pesanan nomor [##], prosesnya:
1. Kami proses dulu dalam [durasi] hari kerja.
2. Dana akan ditransfer ke rekening yang sama dengan pembayaran.
3. Kakak akan menerima notifikasi setelah refund dikirim.

Mohon ditunggu ya, Kak. Kalau ada pertanyaan selama proses, silakan WA saja.
```

### 6. Promotion inquiry

Promotions are emotional — match energy, be specific, include expiry.

Template:
```
Halo Kak! Siap, promonya masih aktif sampai [tanggal] 🎉
Untuk [produk/kategori], diskon [##%] otomatis di checkout.
Kalau mau langsung pesan, saya bantu ya?
```

### 7. Generic / unclear message

Do not guess. Ask ONE clarifying question, not three.

Template:
```
Halo Kak, terima kasih sudah menghubungi kami.
Boleh tolong jelaskan sedikit lebih detail apa yang Kakak butuhkan?
```

## What to avoid

- **No machine-translated English.** "Terima kasih atas pembelian anda" is stiff;
  prefer "Terima kasih sudah belanja di tempat kami".
- **No corporate-speak.** Avoid "Dengan hormat", "Kami sampaikan", "Perkenankan kami
  menginformasikan" unless in Strictly-Formal register.
- **No all-caps.** Even for emphasis.
- **No emoji stacking.** One or two is fine; 🎉🎉🎉🎉🎉 is not.
- **No promising what you don't know.** "Pasti besok sampai" when you can't guarantee
  it. Use "Biasanya 1–2 hari" instead.
- **No passive aggressive.** "Seperti yang sudah diinformasikan sebelumnya..." — just
  re-explain kindly.

## Common phrase catalog

| English | Bahasa (friendly) | Bahasa (formal) |
|---------|-------------------|-----------------|
| Hi / Hello | Halo | Selamat pagi / siang / sore |
| Thanks | Makasih ya | Terima kasih |
| Sorry | Maaf ya | Mohon maaf |
| Please wait | Ditunggu ya | Mohon ditunggu |
| No problem | Santai aja / Gak apa | Tidak apa-apa |
| Let me check | Saya cek dulu ya | Izin kami cek terlebih dahulu |
| Available | Ready / masih ada | Tersedia |
| Out of stock | Habis stok | Stok kosong |
| Confirmed | Siap / beres | Dikonfirmasi |
| Refund | Refund / pengembalian dana | Pengembalian dana |
| Paid | Udah lunas / dibayar | Telah dibayar / dilunasi |

## Output

Produce 1 draft reply by default. If the user asks for alternatives, produce 2–3
drafts clearly labeled with register (`Formal-Friendly`, `Casual-Warm`,
`Strictly-Formal`). Do not include prefaces explaining your choices; just the reply
text, because the operator will copy-paste it directly into WhatsApp.
