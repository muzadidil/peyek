# Buku Peyek — Setup

Satu file: `index.html`. Semua CSS & JS sudah menyatu di dalamnya.

## 1. Buat project Firebase BARU
Jangan pakai project Firestore yang sama dengan Buku Kripik atau project lain.

1. https://console.firebase.google.com → Add project
2. Build → Firestore Database → Create database (mode production)
3. Build → Authentication → Get started → aktifkan **Anonymous**
4. Project settings → Your apps → Web (</>) → copy `firebaseConfig`

## 2. Tempel config
Buka `index.html`, cari bagian `firebaseConfig` (ada komentar besar
"GANTI BAGIAN INI"), ganti semua nilai `GANTI_...` dengan punya Anda.

## 3. Pasang security rules
Firestore Database → Rules → tempel isi file `firestore.rules` → Publish.
Ini penting — tanpa ini database bisa dibaca/ditulis siapa saja yang tahu URL-nya.

## 4. Deploy ke GitHub Pages
1. Buat repo baru, upload `index.html` ke root repo
2. Settings → Pages → aktifkan, custom domain: `peyek.zasha.online`
3. Di DNS zasha.online, tambah CNAME: `peyek` → `muzadidil.github.io`
   (⚠️ jangan diarahkan ke `muzadidil.github.io/nama-repo` — ini
   kesalahan yang pernah kejadian di project sebelumnya)

## Struktur data Firestore
- `bahan` — master bahan (nama, hargaTerakhir)
- `toko` — master toko kulak (nama)
- `belanja` — riwayat belanja (tanggal, toko, items[], total)
- `produksi` — riwayat produksi + hasil kalkulator (bahanItems[], gas, toples, totalModal, hargaPerToples)
- `penjualan` — riwayat penjualan ke konsumen (namaPembeli, qty, hargaJual, total)

## Catatan
- Auth pakai Anonymous — tidak ada halaman login, tapi tetap butuh
  Firestore rules supaya tidak diakses publik.
- Kalau nanti butuh multi-user/login sungguhan, bagian auth ini yang
  perlu diganti duluan.
