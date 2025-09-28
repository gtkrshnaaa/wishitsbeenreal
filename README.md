# Wish It’s Been Real — Static Novel Site

Proyek ini adalah situs statis untuk novel berjudul "Wish It’s Been Real". Situs berisi halaman beranda (sinopsis) dan halaman bab per bagian. Stack yang digunakan sangat sederhana: HTML + CSS murni, tanpa build tools atau framework, sehingga mudah untuk dikembangkan dan di-deploy ke layanan static hosting apa pun.

---

## Fitur

- Navigasi sederhana antara beranda dan halaman bab.
- Desain modern dengan tema gelap, responsif, dan aksesibel.
- Komponen UI dasar: header lengket, kartu konten, tombol aksi, dan footer dinamis dengan tahun berjalan.

---

## Struktur Direktori

```
wishitsbeenreal/
├─ index.html                  # Beranda: sinopsis dan tautan ke Bab 1
├─ css/
│  └─ style.css               # Gaya global untuk seluruh situs
├─ page/
│  └─ section1/
│     ├─ part1.html           # Bab 1 – Part 1 (terisi)
│     └─ part2.html           # Bab 1 – Part 2 (placeholder, perlu konten)
├─ novelguide.md              # Panduan penulisan & timeline cerita
└─ README.md                  # Dokumen ini
```

Catatan cepat:

- `index.html` memuat sinopsis dan link ke `page/section1/part1.html`.
- `css/style.css` berisi variabel CSS, layout, tipografi, komponen, dan responsivitas.
- `page/section1/part1.html` berisi konten naratif lengkap untuk Bab 1 – Part 1.
- `page/section1/part2.html` saat ini kosong dan disiapkan untuk konten lanjutan.
- `novelguide.md` adalah referensi penting untuk konsistensi alur, gaya, dan timeline.

---

## Cara Menjalankan Secara Lokal

Tidak membutuhkan server khusus. Anda bisa langsung membuka file HTML di browser.

Pilihan 1 — Buka file langsung:

1. Buka folder proyek.
2. Klik ganda `index.html` (atau buka melalui menu Open File di browser).

Pilihan 2 — Menggunakan server lokal sederhana (opsional, disarankan untuk navigasi path yang konsisten):

- Dengan Python 3:

  ```bash
  python3 -m http.server 8000
  ```

  Lalu akses: http://localhost:8000/

---

## Panduan Pengembangan Konten

Struktur konten dibagi per "section" (bab) dan "part" (bagian bab). Untuk menambah bab/part baru:

1. Buat folder untuk section (jika belum ada), misal `page/section2/`.
2. Tambahkan file HTML baru, misal `page/section2/part1.html`.
3. Gunakan pola HTML yang konsisten seperti di `page/section1/part1.html`:
   - Sertakan `<link rel="stylesheet" href="../../css/style.css" />` dengan path relatif yang benar.
   - Sertakan header navigasi agar pembaca bisa kembali ke beranda dan bernavigasi antar part.
   - Bungkus konten utama di dalam `<main> → <section class="section"> → <div class="container"> → <article class="card">`.
   - Tambahkan footer dengan tahun dinamis.
4. Perbarui navigasi di `index.html` atau halaman terkait agar tautan ke part baru mudah ditemukan.

Contoh kutipan struktur halaman part:

```html
<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Bab X – Part Y: Judul Bagian</title>
  <!-- English comment for code: use relative path to CSS from nested pages -->
  <link rel="stylesheet" href="../../css/style.css" />
  <meta name="description" content="Ringkasan singkat halaman." />
  <!-- English comment for code: keep meta description concise -->
  </head>
<body>
  <!-- English comment for code: site header with navigation -->
  <header class="site-header"> … </header>

  <main>
    <section class="section">
      <div class="container">
        <article class="card">
          <header class="article-header">
            <h2>Bab X – Part Y: Judul Bagian</h2>
            <p style="color: var(--muted); margin: .4rem 0 0;">Lokasi, Tahun — Waktu • <em>Keterangan</em></p>
          </header>

          <p>Paragraf narasi…</p>

          <footer class="article-footer">
            <a class="btn" href="part{Y+1}.html">Lanjut ke Part berikutnya</a>
          </footer>
        </article>
      </div>
    </section>
  </main>

  <footer class="site-footer"> … </footer>
  <script>
    // English comment: Set current year on page footer
    document.getElementById('year').textContent = new Date().getFullYear();
  </script>
</body>
</html>
```

Tips tambahan:

- Gunakan `meta name="description"` yang spesifik untuk SEO dan cuplikan pratinjau.
- Pastikan path relatif ke `css/style.css` sesuai dengan kedalaman folder.
- Konsultasikan `novelguide.md` untuk konsistensi timeline, tone narasi, dan milestone cerita.

---

## Gaya Penulisan HTML/CSS

- Komentar dalam KODE ditulis dalam bahasa Inggris (contoh sudah diterapkan di HTML/CSS).
- Gunakan kelas utilitas yang sudah ada di `css/style.css`:
  - `container`, `section`, `card`, `site-header`, `site-nav`, `site-footer`, `btn`, `article-header`.
- Variabel warna dan layout tersedia di `:root` (lihat `css/style.css`), contoh: `--bg`, `--text`, `--brand`, `--border`, `--radius`.
- Responsivitas dasar sudah disiapkan di media query `@media (max-width: 680px)`.

---

## Roadmap / TODO

- Isi konten `page/section1/part2.html` (saat ini kosong).
- Tambahkan navigasi untuk Bab/Part berikutnya saat konten bertambah.
- Tambahkan breadcrumb opsional untuk navigasi yang lebih jelas.
- Pertimbangkan menambah halaman "Daftar Isi" jika jumlah part makin banyak.

---

## Cara Deploy (Opsional)

Karena ini situs statis, Anda dapat melakukan deploy di layanan seperti GitHub Pages, Netlify, Vercel, atau Cloudflare Pages dengan langsung menunjuk ke root proyek ini. Tidak ada proses build yang diperlukan.

---

## Lisensi

Tentukan lisensi sesuai preferensi Anda. Jika tidak ditentukan, anggap sebagai "All rights reserved" untuk naskah dan aset terkait.

---

## Kredit

- Penulis & Konsep: Gilang Teja Krishna (Kiann)
- Desain & Implementasi Frontend: Struktur HTML/CSS sederhana berbasis komponen dasar.

