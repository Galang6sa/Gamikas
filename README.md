# KasKelas

Prototipe antarmuka KasKelas untuk tahap M1. Aplikasi ini memakai data contoh fiktif dan berjalan sepenuhnya di browser tanpa backend.

## Menjalankan

Gunakan Node.js 20 atau yang lebih baru.

```sh
npm install
npm run dev
```

Buka `http://localhost:3000`. Akun awal demo adalah siswa Rani (NRP 107), PIN contoh `123456`. Tombol akun di header membuka halaman masuk dan pilihan peran bendahara. Status demo dan pengaturan tersimpan di `localStorage`.

## Perintah pemeriksaan

```sh
npm test
npm run typecheck
npm run build
```

## Isi prototipe

- Beranda siswa dengan karcis tagihan, denah bangku 29 siswa, papan pembayaran, dan rangkaian stempel.
- Alur bayar dengan minggu pilihan, nominal live, QRIS contoh yang tidak aktif, unggah bukti lokal, serta enam hasil simulasi OCR dan jaringan.
- Kas kelas, riwayat pemasukan, pengeluaran, pengaturan tampilan, suara, notifikasi, dan PIN demo.
- Meja bendahara dengan antrean, pratinjau CSV contoh, transaksi tanpa pemilik, input tunai, catat pengeluaran, kebijakan denda, dan tautan WhatsApp.
- Panel waktu demo untuk mengubah tanggal. Tanggal awal dikunci pada 23 Oktober 2026.
- Perhitungan denda murni dan uji kasus pada `lib/domain.test.ts`.

## Struktur

- `app/page.tsx`: alur prototipe, data contoh, dan komponen UI.
- `app/globals.css`: token desain, tema, tata letak responsif, serta aksesibilitas gerak.
- `app/layout.tsx`: metadata, font lokal, dan dokumen bahasa Indonesia.
- `lib/domain.ts`: fungsi tanggal, format rupiah, dan denda.
- `lib/domain.test.ts`: uji unit aturan denda.

## Dependensi

- Next.js, React, dan TypeScript untuk aplikasi App Router bertipe aman.
- Gabarito dan Atkinson Hyperlegible Next dari `@fontsource` agar font tersedia lokal tanpa CDN.
- Vitest 4.1 untuk uji unit logika denda.
- Override PostCSS 8.5.31 untuk menutup temuan audit dependency tree Next.js tanpa menaikkan Next.js ke major yang berbeda.

## Asumsi dan batas prototipe

- Semua nama dan transaksi adalah data fiktif. Angka saldo serta status merupakan data demo agar layar dapat ditinjau.
- Semua login, validasi pembayaran, hasil OCR, impor CSV, rekonsiliasi, notifikasi, dan pencatatan bendahara hanya simulasi browser.
- Gambar QRIS diberi label contoh dan tidak dapat menerima pembayaran.
- Unggahan bukti hanya dipilih di browser; gambar tidak diunggah atau disimpan ke server.
- Perubahan peran tersedia melalui halaman masuk untuk menguji tampilan siswa dan bendahara.
- Tautan WhatsApp hanya membuka `wa.me`; aplikasi tidak mengirim atau memastikan pesan terkirim.
- Tema sistem menjadi pilihan awal; pilihan tema pengguna disimpan di perangkat.

Belum dibangun: backend, autentikasi nyata, OCR sungguhan, impor CSV, sinkronisasi, push notification, ikon PWA terpasang, dan service worker.
