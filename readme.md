# Manten Wedding Organizer

Manten Wedding Organizer adalah aplikasi web untuk menampilkan layanan wedding organizer, mengelola konten bisnis, dan membantu calon klien memilih paket pernikahan secara lebih terstruktur. Project ini terdiri dari frontend berbasis Next.js dan backend REST API berbasis Go.

Aplikasi ini dirancang agar pengunjung dapat melihat informasi layanan secara jelas, memilih paket dan addon yang sesuai, lalu mengirim ringkasan konsultasi melalui WhatsApp. Di sisi admin, aplikasi menyediakan dashboard untuk mengelola konten utama seperti paket, addon, galeri, testimoni, jadwal event, dan pengaturan brand.

<br/>

## Tujuan Project

Project ini dibuat untuk mendigitalisasi proses informasi dan konsultasi wedding organizer. Pengunjung tidak hanya membaca daftar layanan, tetapi juga bisa melakukan simulasi awal dengan memilih paket dan layanan tambahan sebelum menghubungi pihak penyedia jasa.

Dengan adanya panel admin, pemilik bisnis dapat memperbarui konten website tanpa perlu mengubah kode secara langsung. Data seperti harga paket, foto portofolio, testimoni, warna brand, kontak WhatsApp, dan jadwal kegiatan dapat dikelola melalui sistem.

<br/>

## Fitur Utama

### Website Publik

- Halaman beranda yang menampilkan identitas brand, slogan, pengenalan layanan, dan testimoni klien.
- Halaman paket yang menampilkan daftar paket wedding organizer lengkap dengan gambar, deskripsi, benefit, dan rentang harga.
- Halaman detail paket berdasarkan slug, sehingga setiap paket memiliki URL yang mudah dibaca.
- Halaman portofolio berupa galeri foto acara pernikahan dengan informasi pasangan, lokasi, orientasi gambar, status aktif, dan urutan tampil.
- Halaman jadwal kegiatan yang menampilkan event berdasarkan bulan dan tahun.
- Footer dan navigasi yang mengambil data dari pengaturan brand, sehingga informasi kontak dan warna tampilan dapat disesuaikan dari backend.

### Alur Konsultasi

Project ini memiliki alur konsultasi bertahap untuk membantu pengunjung menyusun kebutuhan awal:

1. Memilih paket pernikahan.
2. Memilih addon atau layanan tambahan yang tersedia untuk paket tersebut.
3. Melihat ringkasan pilihan paket dan addon.
4. Mengirim pesan konsultasi otomatis ke WhatsApp.

Pesan WhatsApp dibuat otomatis berdasarkan pilihan pengguna, sehingga calon klien tidak perlu menulis ulang detail paket dan addon yang diminati.

### Dashboard Admin

Dashboard admin digunakan untuk mengelola konten website. Beberapa data yang dapat dikelola meliputi:

- Paket wedding organizer.
- Addon dan kategori addon.
- Relasi addon dengan paket.
- Galeri portofolio.
- Testimoni.
- Jadwal event.
- Pengaturan brand, kontak, logo, slogan, dan warna utama website.

Area admin dilindungi menggunakan autentikasi berbasis JWT. Token disimpan di sisi client dan digunakan untuk mengakses endpoint yang membutuhkan hak admin.

### Upload Media

Backend menyediakan modul upload yang terhubung dengan Supabase Storage. Modul ini digunakan untuk mengunggah aset seperti gambar paket, galeri, logo, atau konten visual lain yang dibutuhkan website.

<br/>

## Teknologi yang Digunakan

### Frontend

- Next.js
- React
- TypeScript
- Tailwind CSS
- Lucide React
- GSAP
- Next Font

Frontend menggunakan App Router Next.js dengan pembagian halaman publik dan halaman admin. Data diambil dari REST API melalui helper fetch terpusat, sehingga konfigurasi base URL dan authorization header lebih mudah dikelola.

### Backend

- Go
- Gin Web Framework
- GORM
- PostgreSQL
- JWT Authentication
- Supabase Storage
- Swagger Documentation
- Docker

Backend dibangun dengan pendekatan modular. Setiap domain utama memiliki folder sendiri yang berisi model, DTO, repository, service, handler, dan routes. Struktur ini membuat kode lebih mudah dirawat karena logika tiap fitur dipisahkan dengan jelas.

### Database

Database menggunakan PostgreSQL dengan migration SQL. Beberapa tabel utama yang digunakan:

- `packages`
- `addons`
- `addon_categories`
- `package_addons`
- `gallery`
- `testimonials`
- `events`
- `settings`

Struktur data menggunakan UUID sebagai primary key, timestamp untuk pencatatan waktu, serta beberapa index untuk membantu pencarian dan pengurutan data aktif.

<br/>

## Arsitektur Project

Project dipisahkan menjadi dua bagian utama:

- Frontend sebagai antarmuka pengguna dan admin.
- Backend sebagai REST API yang mengelola data, autentikasi, upload, dan akses database.

Frontend berkomunikasi dengan backend melalui endpoint `/api`. Untuk kebutuhan browser, tersedia proxy route di Next.js agar request ke backend tetap bisa dikelola dari satu sisi aplikasi frontend.

Backend menggunakan pola berlapis:

- Routes menerima dan mengelompokkan endpoint.
- Handler memproses request dan response HTTP.
- Service menyimpan logika bisnis.
- Repository bertanggung jawab terhadap query database.
- Model merepresentasikan struktur tabel database.
- DTO digunakan untuk bentuk data request dan response.

Pemisahan ini membuat project lebih rapi, mudah dikembangkan, dan lebih aman ketika fitur bertambah.

<br/>

## Repository Project

Beberapa modul API yang tersedia:
- **Frontend**: https://github.com/benayajosuaa/frontend-manten
- **Backend**: https://github.com/benayajosuaa/manten-backend

<br/>

## Keunggulan Project

- Memiliki pemisahan frontend dan backend yang jelas, sehingga pengembangan tampilan dan API dapat dilakukan secara terpisah.
- Menggunakan struktur backend modular, membuat setiap fitur lebih mudah dipahami, diuji, dan dikembangkan.
- Mendukung pengelolaan konten dinamis melalui dashboard admin.
- Menyediakan alur konsultasi bertahap yang praktis untuk calon klien.
- Mengintegrasikan WhatsApp sebagai jalur komunikasi langsung dari hasil pilihan pengguna.
- Mendukung upload media melalui Supabase Storage.
- Menggunakan PostgreSQL dengan migration, UUID, relasi tabel, index, dan timestamp.
- Menggunakan JWT untuk membatasi akses fitur admin.
- Frontend mengambil pengaturan brand dari backend, sehingga warna, kontak, slogan, dan identitas website bisa diperbarui tanpa hardcode di banyak tempat.
- Dokumentasi API tersedia melalui Swagger, sehingga endpoint backend lebih mudah dipahami dan diuji.

<br/>

## Ringkasan

Manten Wedding Organizer adalah project full-stack untuk kebutuhan website wedding organizer yang tidak hanya menampilkan profil layanan, tetapi juga menyediakan sistem pengelolaan konten dan alur konsultasi awal. Dengan kombinasi Next.js, Go, PostgreSQL, JWT, dan Supabase Storage, project ini memiliki fondasi teknis yang cukup kuat untuk dikembangkan menjadi sistem bisnis wedding organizer yang lebih lengkap.
