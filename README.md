# Dokumentasi Template Undangan Digital

Berikut adalah dokumentasi untuk template undangan digital ini, meliputi stack teknologi yang digunakan dan cara melakukan kustomisasi data.

## 🛠️ Tech Stack yang Digunakan

Template ini dibangun menggunakan teknologi web dasar dengan tambahan beberapa library eksternal (pihak ketiga) untuk memperkaya fitur:

1. **HTML5, CSS3, & JavaScript (Vanilla)**: Fondasi utama struktur, gaya, dan interaktivitas halaman.
2. **Bootstrap 5.3.0**: Framework CSS untuk membuat tata letak yang responsif (Grid, Navbar Offcanvas, Card, Form, dll) secara cepat.
3. **Bootstrap Icons**: Digunakan untuk ikon-ikon seperti jam, kalender, dan ikon media sosial.
4. **Google Fonts**: Menggunakan font "Sacramento" (untuk tulisan latin/sambung) dan "Work Sans" (untuk teks paragraf).
5. **simplyCountdown.js**: Library JavaScript untuk membuat fitur hitung mundur (countdown) waktu acara.
6. **bs5-lightbox**: Plugin untuk menampilkan galeri foto dalam bentuk *popup/lightbox* (saat foto diklik).
7. **Disqus**: Platform pihak ketiga yang disematkan untuk fitur kolom komentar/ucapan doa.
8. **Google Apps Script**: Digunakan sebagai *endpoint* untuk menerima data form RSVP (Kehadiran) dan menyimpannya ke Google Sheets.

---

## 📝 Cara Menyesuaikan (Kustomisasi) Data Baru

Semua perubahan data dapat dilakukan langsung di dalam file `index.html`. Berikut panduan per bagiannya:

### 1. Nama Tamu Undangan (Penerima)

Nama tamu tidak ditulis langsung (hardcode) di HTML, melainkan menggunakan **URL Parameter**.

- Contoh URL: `index.html?n=Budi&p=Bapak`
- Script di bagian paling bawah otomatis mengambil parameter `n` (Nama) dan `p` (Sapaan/Pronoun) untuk ditampilkan di bagian Hero.

### 2. Data Mempelai (`<section id="home">`)

- Cari tag `<h3>Sandhika Galih</h3>` dan `<h3>Nofariza</h3>`.
- Ubah nama, nama orang tua, serta deskripsi singkatnya.
- Ganti foto mempelai pada tag `<img src="img/sandhika.png">` dan `<img src="img/nofa.png">`.

### 3. Waktu dan Tempat Acara (`<section id="info">`)

- **Lokasi & Peta**: Ubah teks alamat, lalu ganti link `src` pada tag `<iframe>` dengan tautan semat (embed) Google Maps dari lokasi acara yang baru. Jangan lupa ganti juga link pada tombol "Klik untuk membuka peta".
- **Waktu Akad & Resepsi**: Sesuaikan jam dan tanggal pada elemen `.card` di bagian ini.

### 4. Countdown/Hitung Mundur

- Scroll ke bagian paling bawah sebelum tag `</body>`.
- Cari script `simplyCountdown('.simply-countdown', { ... })`.
- Ubah `year`, `month`, `day`, dan `hours` sesuai waktu acara pernikahan.

### 5. Cerita & Galeri Foto

- **Cerita (`#story`)**: Ubah teks pada *timeline* dan ganti gambar *background* pada `<div class="timeline-image" style="background-image: url(...)">`.
- **Galeri (`#gallery`)**: Ganti atribut `src` (untuk thumbnail) dan atribut `href` (untuk foto ukuran penuh saat di klik) pada setiap tag gambar.

### 6. Form Kehadiran/RSVP (`<section id="rsvp">`)

- Secara default, form diarahkan ke Google Script Sandhika Galih.
- Untuk data baru, Anda perlu membuat **Google Sheets** baru dan menghubungkannya dengan **Google Apps Script** untuk menangani POST request.
- Setelah Script di-*deploy*, salin URL Web App-nya dan tempelkan ke atribut `action="..."` pada tag `<form id="my-form">`.

### 7. Kolom Ucapan/Komentar (Disqus)

- Buat akun dan properti baru di [Disqus](https://disqus.com/).
- Pada script Disqus di bagian `#rsvp`, ubah `this.page.url`, `this.page.identifier`, dan URL script `s.src = 'https://[SHORTNAME-ANDA].disqus.com/embed.js'` dengan data dari akun Disqus Anda.

### 8. Kado Digital / Rekening (`<section id="gifts">`)

- Ganti nama bank, nomor rekening, dan nama pemilik rekening.
- Untuk pembayaran via QR (misal: Saweria, GoPay, OVO), ganti file gambar pada `<img src="img/saweria.png">`.

### 9. Musik Latar/Audio

- Cari tag `<audio id="song">`.
- Ganti file musik pada `<source src="audio/save-and-sound.mp3" type="audio/mp3">` dengan file mp3 Anda sendiri yang diletakkan di folder `audio/`.
