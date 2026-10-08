# Website Masjid Jami' Nurul Hikmah

Website statis + panel admin standalone untuk Masjid Jami' Nurul Hikmah, Dusun Nadri, Desa Krendetan, Kec. Bagelen, Kab. Purworejo, Jawa Tengah.

## Isi File

| File | Fungsi |
|---|---|
| `index.html` | Situs publik (6 halaman: Home, Donatur, Keuangan, Progress Renovasi, Profil, Blog + halaman kustom) |
| `admin.html` | Panel admin (tanpa login): kelola postingan, kategori, halaman, pengaturan infaq, backup, publikasi GitHub |
| `data.json` | Sumber data konten (postingan, kategori, halaman, pengaturan) — dibaca situs publik |
| `laporan-infaq.html` | Laporan perolehan infaq & donatur (live dari Google Sheets + snapshot offline) |
| `laporan-keuangan.html` | Laporan pemasukan/pengeluaran (live dari Google Apps Script) |

## Cara Pakai (Offline / Lokal)

1. Ekstrak semua file ke **satu folder** (jangan dipisah — `index.html` memanggil `laporan-*.html` dan `data.json`).
2. Buka `index.html` di browser.
3. Untuk mengelola konten, buka `admin.html` di browser yang sama.
4. Data tersimpan di browser (localStorage). Gunakan tab **Backup Data** → Ekspor JSON untuk cadangan / pindah perangkat.

## Publish ke GitHub Pages (gratis)

1. Buat repository **public** di GitHub, upload semua 5 file.
2. **Settings → Pages → Source: Deploy from branch** → pilih branch `main`, folder `/ (root)`.
   URL: `https://<username>.github.io/<repo>/`
3. Buat Personal Access Token: **Settings → Developer settings → Personal access tokens → Tokens (classic)** → centang `public_repo` (atau fine-grained: **Contents: Read & write**).
4. Buka `admin.html` → tab **Publikasi GitHub** → isi username, repo, branch, token → Simpan.
5. Alur harian: edit postingan → **Simpan** → **Publikasikan** (commit `data.json` otomatis). Situs publik terbarui ±1–2 menit.

> `admin.html` boleh tidak di-upload (simpan di komputer Anda saja) untuk keamanan token.

## Data Live dari Google Sheets

Tiga komponen mengambil data langsung dari Google Sheets saat halaman dibuka (tidak perlu publish ulang):

- **Halaman Donatur** — laporan infaq (Sheet ID `121xudObLmW5Egxs8INmVLg2tG0qPmYYRBVsD7c8jN9s`).
- **Halaman Keuangan** — via Google Apps Script (`MNH_URL` di dalam file).
- **Blok Infaq di Home** — total donasi dihitung otomatis dari Sheet yang sama, indikator `● LIVE dari Google Sheets`.

**Syarat**: Sheet infaq diset **"Anyone with the link can view"**. Jika gagal, otomatis fallback ke angka statis di `data.json` (field "Dana Terkumpul" di admin).

Catatan: Apps Script keuangan harus di-deploy dengan **"Who has access: Anyone"**.

## Kontak

- Telp/WA: 0815-7887-9961
- Email: renovasinurulhikmahnadri@gmail.com
- Rekening infaq: Bank BRI 6849-01-020766-53-9 a.n. Panitia Renovasi Masjid Jami Nurul Hikmah
