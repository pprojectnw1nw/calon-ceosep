# CalonCEO — Portfolio Website

Website portofolio statis pribadi dengan desain asli CalonCEO, tema gelap/terang, galeri visual, blog **Catatan Perjalanan**, satu pemutar video MP4, dan kontrol BGM manual. Website tetap menggunakan HTML, CSS, dan JavaScript biasa serta kompatibel dengan GitHub Pages.

## Teknologi dan aturan penting

- HTML5, CSS3, dan JavaScript vanilla; tidak membutuhkan framework, Node.js, build step, database, backend, atau login.
- Palet warna, tipografi, layout, animasi, menu mobile, galeri, lightbox, dan tema lama dipertahankan.
- Konten baru yang paling sering diedit dikumpulkan di `js/content.js`.
- BGM tidak autoplay dan baru mulai setelah pengunjung menekan tombol. Video juga tidak autoplay.
- Belum ada video atau musik pribadi yang disertakan. Isi URL milik sendiri sebelum mempublikasikannya.

## Struktur file akhir

```text
calonceo/
├── index.html                 # struktur dan bagian-bagian halaman
├── css/
│   └── style.css              # desain asli + gaya blog/video/BGM responsif
├── js/
│   ├── content.js             # EDIT KONTEN BARU: artikel, video, dan BGM
│   └── script.js              # logika tema, menu, blog, pemutar, galeri, kontak
├── audio/
│   └── README.md              # petunjuk MP3 lokal (opsional)
├── videos/
│   └── README.md              # petunjuk hosting video MP4
├── images/
│   ├── README.md
│   └── photography/
│       └── README.md
├── README.md
├── PROJECT_STATUS.md
├── CHANGELOG.md
└── .gitignore
```

## Bagian yang perlu diedit

| Tujuan | File | Yang perlu diubah |
|---|---|---|
| Artikel blog, judul/tanggal/ringkasan/isi/sampul | `js/content.js` | Array `blogPosts` |
| Video pilihan | `js/content.js` | `featuredVideo.title`, `description`, `url`, opsional `poster` |
| BGM | `js/content.js` | `backgroundMusic.title`, `url`, `initialVolume`, label tombol |
| Link kontak lama | `js/script.js` | `siteConfig.links` di bagian atas |
| Foto dan galeri Videography lama | `js/script.js` | `photographyItems` / `videographyItems` |
| Tulisan halaman lama | `index.html` | Edit teks yang sudah ada, jangan hapus tag atau ID sembarangan |
| Warna, jarak, tata letak | `css/style.css` | Variabel di awal file dan aturan komponen |

**Jangan perlu mengubah** `setUpBlog`, `setUpFeaturedVideo`, atau `setUpBackgroundMusic` di `js/script.js` ketika hanya ingin mengganti konten. Fungsi tersebut adalah logika pemutar dan artikel.

## Mengelola blog lewat browser HP Android

### 1. Menambah artikel

1. Buka repository GitHub di browser HP, lalu buka file `js/content.js`.
2. Tekan ikon pensil **Edit this file**.
3. Cari bagian `blogPosts: []`.
4. Salin contoh artikel pada komentar di bawah konfigurasi, lalu tempel objeknya ke dalam array. Hapus tanda komentar jika menyalin seluruh blok contoh.
5. Pastikan objek diletakkan di antara tanda `[` dan `]`. Jika menambah lebih dari satu artikel, pisahkan setiap objek dengan koma.
6. Ganti semua teks contoh dengan kisah atau pengalaman yang benar-benar ingin kamu publikasikan.
7. Di bawah halaman GitHub, pilih **Commit changes** untuk menyimpan.

Contoh bentuk sederhananya:

```js
blogPosts: [
  {
    slug: "pengalaman-belajar-pertama",
    title: "Pengalaman Belajar Pertama",
    date: "2026-10-15",
    category: "Perjalanan belajar",
    summary: "Ringkasan pendek yang menjelaskan isi tulisan.",
    cover: "",
    content: [
      { type: "paragraph", text: "Tulis paragraf pembuka di sini." },
      { type: "heading", text: "Hal yang kupelajari" },
      { type: "paragraph", text: "Tulis isi cerita berdasarkan pengalaman asli." },
      { type: "list", items: ["Pelajaran pertama", "Pelajaran kedua"] }
    ]
  }
]
```

Contoh di atas hanya contoh format, bukan klaim pengalaman pribadi. Gunakan slug unik dengan huruf kecil, angka, dan tanda hubung. Format tanggal harus `YYYY-MM-DD`; tanggal boleh dikosongkan atau dihilangkan bila tidak ingin ditampilkan. Jenis konten yang didukung: `paragraph`, `heading`, `quote`, dan `list`.

### 2. Mengedit artikel

Cari objek dengan `slug` artikel yang mau diubah, lalu edit `title`, `date`, `category`, `summary`, dan `content`. Jangan mengubah nama properti seperti `title`, `summary`, atau `content` karena kode bergantung padanya.

### 3. Menghapus artikel

Hapus seluruh objek artikel yang diinginkan, termasuk koma pemisahnya. Jangan menghapus kurung siku pembuka dan penutup array `blogPosts`.

### 4. Menambahkan gambar sampul

1. Buat folder `images/artikel/` melalui GitHub (menu **Add file → Create new file**, gunakan nama file seperti `images/artikel/.gitkeep` jika GitHub perlu path untuk membuat folder). Lebih mudah: unggah gambar ke folder yang sudah ada seperti `images/`.
2. Unggah gambar milik sendiri, misalnya `sampul-belajar.jpg`.
3. Pada objek artikel, isi `cover` dengan path relatif dari root repository, contohnya `images/sampul-belajar.jpg`.
4. Isi `coverAlt` dengan deskripsi visual singkat untuk aksesibilitas (opsional). Kosongkan `cover: ""` jika artikel tidak memakai gambar.

Gunakan file JPG, PNG, atau WebP yang sudah dioptimalkan. Gambar yang tidak bisa dimuat akan diabaikan atau disembunyikan; layout tetap bekerja.

## Hosting video MP4 — metode utama: Cloudinary

Video 720p ukuran 50–100 MB kurang cocok disimpan langsung di repository. Unggahan file lewat browser GitHub dibatasi **25 MiB per file**. Cloudinary saat ini menawarkan paket gratis dengan **batas maksimum video 100 MB** dan **25 kredit per bulan**. Kreditnya dipakai bersama untuk penyimpanan, bandwidth video, dan transformasi, sehingga bukan berarti 25 GB untuk setiap jenis penggunaan. Simpan file di bawah batas unggahan (lebih aman jika tidak persis 100 MB) dan periksa pemakaian jika pengunjung mulai banyak.

Referensi resmi: [Cloudinary paket dan batas ukuran](https://cloudinary.com/pricing/compare-plans), [dokumentasi upload](https://cloudinary.com/documentation/upload_images), [URL delivery video](https://cloudinary.com/documentation/video_manipulation_and_delivery), [batas unggah GitHub](https://docs.github.com/en/repositories/working-with-files/managing-large-files/about-large-files-on-github).

### 1. Mengunggah dari HP

1. Siapkan file MP4 pribadi di HP. Periksa ukuran file dan pastikan kamu berhak memublikasikannya.
2. Buka situs Cloudinary di browser Android dan buat/login ke akun sendiri. Proyek ini tidak membuat akun atau mengunggah file atas nama kamu.
3. Dari dashboard, buka **Media Library** lalu pilih **Upload** (nama tombol mungkin sedikit berubah mengikuti antarmuka Cloudinary).
4. Pilih video dari aplikasi Files/Galeri, lalu tunggu unggahan selesai. Jaringan stabil sangat membantu untuk file besar.
5. Buka detail aset video dan salin **delivery URL**. Pastikan itu URL media, bukan URL dashboard/pratinjau.

### 2. Mengenali URL video langsung

Bentuk URL Cloudinary umumnya seperti berikut (ini pola, bukan URL video sungguhan):

```text
https://res.cloudinary.com/NAMA_CLOUD/video/upload/v1234567890/nama-video.mp4
```

URL video harus menggunakan HTTPS dan menunjuk ke file MP4—biasanya berakhiran `.mp4`. Jangan menaruh password/API secret di repository. Tidak perlu menambahkan SDK Cloudinary ke website ini.

### 3. Menghubungkan video ke website

1. Buka `js/content.js` di GitHub, tekan ikon pensil.
2. Cari `featuredVideo`.
3. Isi `title`, `description`, dan `url`; tempel URL delivery yang sebenarnya di `url`.
4. Opsional, unggah thumbnail ke repository atau layanan gambar dan isi `poster` dengan path/URL HTTPS-nya.
5. Simpan menggunakan **Commit changes**. Pemutar menggunakan `<video controls playsinline preload="metadata">`, menjaga rasio 16:9, dan tidak autoplay.

Contoh konfigurasi (ganti URL contoh dengan URL milik sendiri):

```js
featuredVideo: {
  title: "Karya Videografi Saya",
  description: "Deskripsi singkat video ini.",
  url: "https://res.cloudinary.com/NAMA_CLOUD/video/upload/v1234567890/nama-video.mp4",
  poster: "images/sampul-video.jpg"
}
```

**Jangan publikasikan URL contoh di atas sebagai media sungguhan.** Jika URL masih kosong atau tidak valid, website menampilkan placeholder. Jika URL gagal dibuka, pemutar menampilkan pesan kegagalan dan halaman lainnya tetap dapat dipakai.

Jika video melebihi batas atau lalu lintas pemutaran menjadi tinggi, kompres MP4 atau pertimbangkan layanan video lain. YouTube/Vimeo dapat menjadi alternatif untuk konten yang cocok diputar melalui embed resmi, tetapi URL halaman mereka bukan URL MP4 langsung dan tidak boleh ditempel ke `featuredVideo.url`.

## Menambahkan BGM (MP3)

Musik latar dikelola terpisah dari audio video. Musik tidak autoplay, memakai `loop` dan `preload="none"`, serta baru mulai setelah pengunjung menekan tombol **Putar musik**. Tombol **Jeda musik** dan slider volume mengontrol audio latar saja; audio video tidak dicampur atau dikendalikan otomatis.

### Opsi A — file MP3 kecil di repository

1. Gunakan musik buatan sendiri atau file yang izinnya sudah kamu pastikan.
2. Buka folder `audio/` di GitHub dan unggah file, misalnya `musik-latar.mp3`.
3. Buka `js/content.js`, lalu isi `backgroundMusic.url` dengan `audio/musik-latar.mp3`.
4. Edit judul atau volume awal (`0` hingga `1`) sesuai kebutuhan.

### Opsi B — host MP3 di layanan media

Unggah MP3 ke layanan yang menyediakan URL file audio langsung melalui HTTPS. Jika menggunakan Cloudinary, audio diperlakukan sebagai aset tipe `video`; salin delivery URL yang berakhiran `.mp3`. Tempel URL tersebut ke `backgroundMusic.url`.

Contoh konfigurasi:

```js
backgroundMusic: {
  title: "Musik latar pribadi",
  url: "audio/musik-latar.mp3",
  initialVolume: 0.25,
  playLabel: "Putar musik",
  pauseLabel: "Jeda musik"
}
```

`initialVolume: 0.25` berarti 25%. Jika URL kosong atau bukan MP3 langsung, kontrol tetap nonaktif dan website memberi petunjuk. File audio gagal dimuat akan menampilkan status, bukan menjalankan musik lain.

## Mengelola konten lama

- **Kontak:** buka `js/script.js` dan edit objek `siteConfig.links` dekat bagian paling atas. Biarkan nilai kosong untuk link yang belum siap dipublikasikan.
- **Foto:** array `photographyItems` ada di `js/script.js`. Taruh gambar di `images/photography/` dan isi path relatif.
- **Galeri video tambahan:** array `videographyItems` yang lama tetap ada di `js/script.js`. Bagian ini terpisah dari Video Pilihan yang baru.
- **Project/About/Skills/Pencapaian:** teks utamanya berada di `index.html`. Jangan mengganti `id` tanpa memperbarui tautan navigasi yang sesuai.
- **Tampilan:** `css/style.css`. Fitur baru menggunakan variabel warna dan radius dari tema lama.

## Upload perubahan melalui GitHub di HP Android

1. Buka repository di browser dan pastikan berada pada branch yang dipakai GitHub Pages.
2. Untuk mengubah file, buka file → ikon pensil → edit → **Commit changes**.
3. Untuk menambah aset kecil, buka folder tujuan → **Add file → Upload files** → pilih file → **Commit changes**. Jika membuat folder baru, gunakan **Add file → Create new file** dan ketik path seperti `images/artikel/contoh.jpg` saat mengunggah/menyusun file jika opsi tersebut tersedia.
4. Hindari mengunggah video 50–100 MB lewat browser GitHub; gunakan Cloudinary.
5. Pastikan `index.html` berada di root repository proyek, sejajar dengan folder `css/`, `js/`, `images/`, `videos/`, dan `audio/`.

## Mengaktifkan dan menguji GitHub Pages

1. Buka **Settings → Pages** di repository.
2. Pilih **Deploy from a branch**, branch `main` (atau branch aktif yang benar), folder `/(root)`, lalu simpan.
3. Buka URL yang diberikan GitHub Pages dan tunggu sampai deployment berstatus berhasil.
4. Uji halaman publik, bukan hanya pratinjau editor GitHub. Perubahan mungkin tidak langsung muncul karena proses deployment atau cache browser.
5. Jika repository bukan bernama `<username>.github.io`, URL biasanya memuat nama repository. Website menggunakan path relatif agar bisa dipakai di root repository maupun subpath GitHub Pages.

### Checklist sebelum dipublikasikan

- [ ] Ganti placeholder konfigurasi dengan artikel dan deskripsi pribadi yang benar.
- [ ] Periksa izin publikasi semua gambar, video, dan musik.
- [ ] Isi URL MP4 langsung pada `featuredVideo.url` dan pastikan video tampil.
- [ ] Isi URL MP3 langsung pada `backgroundMusic.url`; pastikan musik tetap mati sebelum tombol ditekan.
- [ ] Uji tombol Putar/Jeda, volume, kontrol video, tombol kembali artikel, dan navigasi.
- [ ] Periksa mode terang/gelap serta ukuran layar HP.
- [ ] Buka DevTools Console/Network jika tersedia dan periksa error/path 404.
- [ ] Pastikan tidak ada token, password, API secret, atau detail pribadi yang tidak ingin dipublikasikan.

## Troubleshooting cepat

| Masalah | Yang perlu diperiksa |
|---|---|
| Artikel tidak tampil | Pastikan objek berada di dalam `blogPosts: [ ... ]`, koma/kurung valid, ada `slug`, `title`, `summary`, dan `content`. |
| Tombol artikel tidak membuka isi | Pastikan `slug` unik dan hanya memakai huruf/angka/tanda hubung; pastikan `content` berupa array. |
| Gambar sampul tidak muncul | Pastikan ejaan nama/path dan huruf besar-kecil sama, file sudah di-commit, serta URL eksternal HTTPS. |
| Video tidak bisa diputar | Gunakan URL delivery langsung berakhiran `.mp4`, akses publik HTTPS, dan format MP4 yang kompatibel; URL halaman preview tidak bekerja. |
| Musik tidak berbunyi | Pastikan URL berakhiran `.mp3`, bisa diakses tanpa login, format audio valid, volume tidak nol, dan tekan tombol Putar. Browser dapat menolak file yang tidak dapat diakses. |
| Tidak bisa unggah MP4 ke GitHub | Batas unggah browser GitHub adalah 25 MiB per file. Host video di Cloudinary atau kompres ke ukuran kecil. |
| CSS/JS/gambar 404 di GitHub Pages | Jangan gunakan path yang dimulai `/` untuk aset proyek. Gunakan `css/style.css`, `js/content.js`, `images/nama.jpg`, atau path relatif sesuai letak file. |
| Perubahan belum tampil | Pastikan commit tersimpan, deployment Pages selesai, refresh halaman, lalu bersihkan cache browser bila perlu. |
| BGM mengulang dari awal ketika pindah bagian | Navigasi bagian memakai hash dalam halaman ini; audio tidak diinisialisasi ulang saat berpindah artikel/bagian. Jangan menggandakan tag `<audio>`. |

## Status deployment

Proyek ini belum dihubungkan ke akun Cloudinary, URL media pribadi, repository pengguna, atau deployment publik dalam perubahan ini. Pemutar video/BGM akan tetap menampilkan placeholder sampai URL yang benar diisi. Pengujian lokal dijelaskan di `PROJECT_STATUS.md`.
