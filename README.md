# Benefit Akun Kampus Unsrat

Situs statis berisi daftar layanan gratis & diskon yang bisa diklaim dengan akun kampus
**@student.unsrat.ac.id** (Google Workspace) — dilengkapi deskripsi benefit, cara klaim,
dan tautan resmi penyedia.

> Bukan situs resmi Universitas Sam Ratulangi.

## Isi

- 132 layanan dalam 10 kategori dan 4 tier (S/A/B/C) — hasil kurasi dari 146 kandidat
  riset; 14 yang tidak memenuhi/tidak terkonfirmasi tidak ditampilkan
- Tiap kartu menampilkan deskripsi benefit; tombol **Detail** berisi benefit lengkap,
  cara klaim, dan tautan resmi
- Tombol **Kunjungi** membuka situs penyedia (tab baru)
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
services.json   # dataset hasil riset (146 record: status kelayakan, kutipan bukti, catatan —
                # dipakai untuk kurasi; situs menampilkan 132 yang berpeluang diklaim)
assets/
  favicon.svg   # ikon tab
  fonts/        # Fraunces + Plus Jakarta Sans (Google Fonts, disimpan lokal)
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

Status kelayakan diisi dari halaman edukasi/student **resmi milik penyedia** (bukan blog
atau agregator) pada 11/11/2026 — hanya halaman publik, tanpa login/registrasi. Data riset
lengkap (status + kutipan bukti + URL) tersimpan di `services.json`; situs hanya
menampilkan layanan yang berpeluang diklaim beserta deskripsi benefitnya.
Ilustrasi peta di hero memakai geometri Natural Earth (public domain) yang diwarnai
ulang sesuai tema situs.

## Disclaimer

Bukan situs resmi Universitas Sam Ratulangi. Status & kutipan diambil dari halaman resmi
penyedia pada 11/11/2026; benefit bisa berubah sewaktu-waktu — selalu cek syaratnya di
situs penyedia.
