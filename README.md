# Benefit Akun Kampus Unsrat

Situs statis berisi daftar layanan gratis & diskon yang bisa diklaim dengan akun kampus
**@student.unsrat.ac.id** (Google Workspace) — lengkap dengan status kelayakan, metode
verifikasi, dan kutipan bukti dari halaman resmi penyedia.

> Bukan situs resmi Universitas Sam Ratulangi.

## Isi

- 146 layanan dalam 10 kategori dan 4 tier (S/A/B/C)
- Status per layanan: `terbukti_diterima`, `kemungkinan`, `perlu_dokumen`,
  `tidak_diketahui`, `tidak_memenuhi`
- Tombol **Bukti** di tiap kartu menampilkan kutipan resmi + URL sumber;
  **Kunjungi** membuka situs penyedia (tab baru)
- Filter: pencarian, kategori, dan tier (minimal 1 tier harus tetap aktif)

## Menjalankan lokal

Tanpa build step, tanpa dependensi — murni HTML/CSS/JS:

```bash
# cara 1: buka langsung (sudah dites via file://)
xdg-open index.html

# cara 2: server lokal
python3 -m http.server 8000     # lalu buka http://localhost:8000
```

## Struktur

```
index.html      # seluruh situs: CSS + JS + data inline; bisa dibuka tanpa server
services.json   # dataset 146 layanan (bentuk file; salinan yang dipakai situs ada inline di index.html)
assets/
  favicon.svg   # ikon tab
  fonts/        # Archivo (Google Fonts, disimpan lokal)
  logos/        # 140 favicon PNG (fallback runtime: google s2 favicons -> inisial)
```

**Edit data:** data yang dirender situs ada di objek `const SERVICES = [...]` di dalam
`index.html`. `services.json` adalah salinan dataset yang sama (untuk dibaca tooling
lain); kalau salah satu diubah, samakan keduanya.

## Deploy

- **Vercel** — import repo ini di dashboard (Framework Preset: *Other*, Build Command &
  Output Directory dikosongkan), atau dari folder ini: `npx vercel` lalu `npx vercel --prod`.
  Setiap `git push` ke `main` otomatis re-deploy.
- **GitHub Pages** — Settings → Pages → Deploy from branch `main`, folder `/ (root)`.

## Metodologi data (tanggal cek 11/11/2026)

Status diisi dari halaman edukasi/student **resmi milik penyedia** (bukan blog atau
agregator). Hanya halaman publik — tanpa login, tanpa registrasi. Setiap entri memuat
kutipan verbatim + URL; arti tiap status ada di footer situs.

## Disclaimer

Bukan situs resmi Universitas Sam Ratulangi. Status & kutipan diambil dari halaman resmi
penyedia pada 11/11/2026; benefit bisa berubah sewaktu-waktu — selalu cek syaratnya di
situs penyedia. Desain terinspirasi [udayana.my.id](https://udayana.my.id).
