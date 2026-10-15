# Changelog

Perubahan penting untuk proyek CalonCEO dicatat di file ini. Format mengikuti prinsip Keep a Changelog secara sederhana.

## [0.1.0] — 2026-10-14

### Added
- Membuat halaman awal portofolio CalonCEO dengan hero, about, proyek, skills, pencapaian, visual work, kontak, dan footer.
- Menambahkan mode gelap/terang dengan preferensi tema tersimpan secara lokal.
- Menambahkan menu responsif, reveal animation yang menghormati `prefers-reduced-motion`, dan tahun footer otomatis.
- Menambahkan pratinjau poster dengan fallback saat file poster belum disediakan.
- Menambahkan galeri Photography & Videography berbasis array konten yang terpisah.
- Menambahkan dialog pratinjau ukuran penuh untuk gambar.
- Menambahkan dokumentasi konfigurasi konten, testing, GitHub Pages, dan panduan domain kustom.

### Notes
- Foto, video, link GitHub, dan kontak personal belum diisi karena data/aset asli belum disediakan.
- Belum dipublikasikan ke GitHub Pages dan domain `calonceo.my.id` belum dihubungkan.

## [0.2.0] — 2026-10-15

### Added
- Menambahkan bagian Catatan Perjalanan dengan daftar artikel, tampilan baca artikel, tanggal, ringkasan, sampul opsional, konten terstruktur, dan navigasi kembali.
- Memisahkan konfigurasi artikel, video pilihan, dan BGM ke `js/content.js` agar mudah diedit lewat GitHub di HP.
- Menambahkan pemutar MP4 HTML5 responsif dengan `controls`, `playsinline`, `preload="metadata"`, validasi URL langsung, dan placeholder/error state.
- Menambahkan kontrol BGM dengan Play/Pause, status aksesibel, slider volume, `loop`, `preload="none"`, dan keadaan mati/nonaktif ketika URL belum disetel.
- Menambahkan gaya responsif yang mengikuti token warna, border, radius, dan surface desain asli.
- Memperbarui README dan panduan folder media untuk workflow Android/GitHub Pages.

### Notes
- Konten artikel awal kosong untuk menghindari mengarang pengalaman pribadi. Video dan MP3 pribadi juga belum dihubungkan.
- Cloudinary dipilih sebagai metode utama video; unggah media dan uji URL harus dilakukan sendiri oleh pemilik sebelum publikasi.
