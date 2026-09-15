# Jawaban Latihan — [Muhammad Putra Perdana Nurvianto] / [224180596]

## Latihan 1 — Rasakan bug-nya
| No | Pesan error | Penyebab |
|---|---|---|
| 1 | bodynya kosong/error 500 |express.json() dihapus jadi Express gak parsing body-nya, req.body jadinya undefined bukan object|
| 2 | 404 Not Found — body: { "msg": "Buku dengan id 1 tidak ditemukan" } | Number() dihapus, jadi b.id (angka) dibanding sama req.params.bukuId (string) pake === |
| 3 | requestnya ga dapet response yang bener|return dihapus jadi setelah res.status(404).json(...) kekirim |
| 4 | 04 Not Found — body: { "msg": "Buku dengan id statistik tidak ditemukan" } |Urutan route ketuker, /:bukuId di atas nangkep duluan "statistik" jadi dianggap id, terus di Number() hasilnya NaN |

## Latihan 4 — Kenapa 409 dan bukan 400?

400 dipake kalau yang salah adalah bentuk requestnya field kurang, tipe data salah, format gak sesuai , kalo pake 409 (Conflict), karena requestnya benar tapi bentrok sama state resourcenya.

## Latihan 8 — Refleksi
### 1. Kenapa `?keyword=zzz` 200 tapi `/buku/999` 404?

buku/999 minta satu buku spesifik lewat params dan buku itu emang gak ada jadi 404. Sedangkan /buku?keyword=zzz itu tetep manggil endpoint / buku yang jelas ada, cuma hasil pencariannya aja yang kosong.

### 2. Kenapa hapus buku berstok itu 409?

karena requestnya sendiri valid, yang bentrok itu kondisi datanya (masih ada stok), bukan salah format.

### 3. Kalau pindah ke MySQL, file mana yang berubah?

Yang keubah cuma data/buku.js (diganti jadi model Sequelize, bukan array lagi) sama isi function-function di controllers/buku.js yang tadinya main array (find, filter, push) diganti jadi query ke database.

### 4. Apa yang berlebihan dari project ini?

Terasa agak lebih rumit 