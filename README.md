# Unggul Prediction — ramalabs

**Aplikasi asesmen kecukupan dan review Formulir Evaluasi Diri (FED) LAMSPAK IAPS 2.0 Unggul Program Sarjana.** Satu situs web statis siap unggah ke GitHub Pages. Tidak memerlukan server aplikasi, database, token, atau API eksternal.

## Sumber materi dan ketepatan fungsi

Dibuat dari tiga berkas yang diberikan pengguna:

1. ZIP `14_IAPS-2.0-Unggul_Sarjana(1).zip`, berisi `FED_Unggul_Sarjana.docx` (template formulir, belum terisi), `14_Matriks Penilaian Unggul_Sarjana.pdf` (16 halaman, 73 butir, skor 0–2, bobot), dan `Alat Bantu Penghitungan Tabel.xlsx` (alat bantu tabel).
2. Dua XLSX contoh hasil asesmen dengan struktur `Menu`, `Kertas Kerja`, `Hasil Penilaian`, dan `Laporan`. Keduanya hanya menjadi rujukan struktur dan gaya deskripsi penilaian; **data identitas, skor, dan narasi contoh tidak disertakan dalam aplikasi yang akan dipublikasikan**.

Dari matriks: **73 butir**, jumlah bobot **141**, nilai maksimum **282**. Lima indikator syarat perlu Unggul yang ditandai pada contoh `Hasil Penilaian` adalah **9, 16, 55, 56, dan 60**. Skor terbobot tiap indikator = skor asesor × bobot. Beberapa indikator secara eksplisit tidak memiliki nilai kurang dari 1. Aplikasi menonaktifkan opsi skor 0 bagi indikator tersebut.

**Pembaruan: indikator hasil akreditasi otomatis (SIMULASI).** Setelah seluruh **73 butir** diberi skor, aplikasi menghitung kategori **Terakreditasi Unggul, Terakreditasi, atau Tidak Terakreditasi** berdasarkan Tabel 2 *Sistem dan Acuan Penilaian Akreditasi Unggul Program Studi Sarjana*, Lampiran 29 LAMSPAK (11 Oktober 2024), yang memuat ketentuan NA ≥ 141, pemenuhan 5 syarat perlu, dan larangan skor 0. Sebelum semua skor diisi, status adalah **Belum Final**, termasuk apabila sebagian skor sudah bernilai 0.

**Catatan penting tentang versi aturan:** Dokumen instrumen IAPS 2.0 yang diunggah pengguna memuat 73 rubrik per butir dan bobot; dokumen [LAMSPAK Buku B IAPS 2.0 yang diterbitkan Januari 2026](https://www.lamspak.id/wp-content/uploads/2026/01/B-Kriteria-Indikator-Prosedur-Asesmen-dan-Penilaian-Akreditasi-IAPS-2.0.pdf) mengonfirmasi kategori tiga status dan lima syarat perlu. Acuan Tabel 2 dengan ambang numerik **141** tersedia pada [Lampiran 29 LAMSPAK](https://www.lamspak.id/wp-content/uploads/2025/01/Lampiran-29-Instrumen-Akreditasi-untuk-Perolehan-Status-Terakreditasi-Unggul-Sistem-dan-Acuan-Program-Studi-Sarjana.pdf) (dokumen bertanggal 2024). Karena dokumen berasal dari periode berbeda, **hasil aplikasi adalah simulasi interpretasi dan bukan penetapan akreditasi resmi**. Cocokkan dengan instrumen dan peraturan LAMSPAK terbaru yang berlaku untuk jenis usulan program studi Anda.

## Fitur

- **Dashboard dan indikator status:** skor berbobot 0–282, jumlah item dinilai, kelengkapan bukti, indikator skor nol, lima syarat perlu Unggul, serta tiga kartu hasil status dengan satu kategori aktif (ketika seluruh 73 butir lengkap).
- **Asesmen per butir:** 73 indikator dengan kriteria penilaian skor 2/1/0, bobot, halaman matriks dan standar asal. Kolom bukti FED, lokasi dokumen, catatan kritis, skor asesor, narasi asesor, serta ekspor.
- **Penghitung ambang numerik:** beberapa butir numerik memiliki kalkulator sederhana untuk **saran skor bersyarat**. Hasil harus dikonfirmasi asesor setelah memverifikasi data dan kondisi khusus. Butir kompleks tetap dinilai manual.
- **Impor Excel `.xlsx`:** membaca skor dan narasi pada lembar `Kertas Kerja` dengan pola format dua file contoh. Anda dapat mengubah kembali hasil impor.
- **Baca FED `.docx` atau `.zip` berisi DOCX:** mengekstrak teks **di browser**, menampilkan calon cuplikan yang cocok dengan indikator. Template FED kosong yang sama persis dengan dokumen sumber dikenali dan tidak diperlakukan sebagai bukti. Pencocokan istilah bukan bukti validitas dan **tidak otomatis memberi skor**.
- **Backup JSON, restore JSON, CSV, Word DOCX asli, cetak atau simpan PDF A4**, termasuk kategori dan narasi alasan hasil asesmen.
- **Privasi:** data disimpan dengan `localStorage`. File DOCX/XLSX diproses pada perangkat pengguna tanpa dikirim ke server. Gunakan HTTPS GitHub Pages dan simpan backup terenkripsi secara terpisah apabila terdapat data sensitif.

### Keterbatasan

1. Dokumen FED yang terdapat di ZIP sumber merupakan **template belum terisi**. Aplikasi tidak memuat angka dan temuan program studi baru secara otomatis.
2. Penyusunan narasi bersifat **berbasis aturan** yang menggabungkan skor, kriteria matriks, dan bukti/catatan yang benar-benar dimasukkan. Aplikasi tidak dapat melakukan verifikasi substantif penuh terhadap validitas dokumen, masa berlaku, sampel, atau kepatuhan lembaga.
3. Ekstraksi FED hanya mendukung DOCX (langsung atau di dalam ZIP), bukan PDF pindai. Data kuantitatif yang menggunakan rumus gabungan perlu dicocokkan dengan alat bantu tabel dan dokumen pendukung.
4. Jika web browser tidak mendukung `DecompressionStream('deflate-raw')`, fitur impor DOCX/XLSX mungkin tidak berfungsi; gunakan browser modern atau masukkan data secara manual.
5. Jangan mengunggah file Excel/FED berisi informasi rahasia sebagai aset repository publik; lakukan **impor dari browser setelah situs diterbitkan**.

## Aturan simulasi penetapan kategori

| Kondisi setelah semua 73 butir dinilai | Status simulasi |
|---|---|
| NA ≥ 141, lima syarat perlu (butir 9, 16, 55, 56, 60) = 2, tidak ada skor 0 | **Terakreditasi Unggul** |
| Tidak ada skor 0, tetapi NA kurang dari 141 atau satu/lebih syarat perlu belum mencapai 2 | **Terakreditasi** |
| Ada satu/lebih indikator bernilai 0, terlepas dari total NA | **Tidak Terakreditasi** |
| Setidaknya satu dari 73 indikator belum dinilai | **Belum Final** — belum dinyatakan salah satu dari tiga kategori |

Meskipun kategori ditampilkan setelah seluruh skor terisi, **isi dan kualitas bukti tetap perlu diverifikasi** oleh asesor dan proses akreditasi resmi. Hal ini terutama relevan jika skor diimpor dari Excel tanpa dokumen FED pendukung.

### Kecocokan dengan dua file Excel yang diberikan

- Excel `ak-5812...20260921...xlsx` (unggahan ulang): **NA 209/282**, ada indikator nilai 0, syarat perlu belum terpenuhi → **Tidak Terakreditasi**.
- Excel `ak-8aa785...20261002...xlsx` (unggahan ulang): **NA 233/282**, tidak ada nilai 0, satu syarat perlu (butir 56) memperoleh 1 → **Terakreditasi**.

Angka diperiksa pada sel rekap `Hasil Penilaian!G4:G7` pada kedua file asli, **tidak disertakan dalam ZIP aplikasi publik**.

## Publikasikan di GitHub Pages

1. Unduh ZIP hasil, ekstrak seluruh berkas, **unggah isi ZIP** ke *root* repository GitHub (jangan unggah ZIP tunggal saja). Pastikan `index.html`, `rubric.js`, `core.js`, `app.js`, `zip-import.js`, `styles.css`, `docx-export.js`, dan folder `.github/workflows/` semuanya berada pada lokasi yang benar.
2. Buat repository publik misalnya `unggul-prediction-ramalabs` dan commit berkas ke `main`.
3. Buka **Settings → Pages → Build and deployment → Source: GitHub Actions**.
4. Workflow di `.github/workflows/deploy.yml` akan memvalidasi instrumen dan perhitungan, membangun folder `dist/` secara otomatis, lalu menerbitkan **hanya berkas aplikasi** (tanpa file FED/Excel contoh). Pantau tab **Actions** sampai sukses.
5. URL: `https://USERNAME.github.io/unggul-prediction-ramalabs/`.

## Proses asesmen yang disarankan

Mulai dari mengisi identitas → unggah FED asli jika tersedia → untuk tiap item tinjau kandidat bukti, verifikasi dengan dokumen sumber/tabel/lampiran → isi catatan bukti dan keterbatasan → tetapkan skor sesuai rubrik → klik **Susun deskripsi dari bukti**, koreksi dan perjelas → lihat rekap dan syarat perlu → unduh Word/PDF/CSV serta backup JSON.

**Copyright © [2026] ramalabs. All rights reserved.**

## Pemeriksaan mandiri

Jalankan `node scripts/validate.mjs`, `node scripts/test-status.mjs`, dan `node scripts/build-pages.mjs` pada direktori proyek untuk mengecek rubrik dan menyiapkan berkas statis. Tidak diperlukan `npm install`. Setelah build, folder `dist/` berisi situs siap tayang.
