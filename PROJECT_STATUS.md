# Project Status — CalonCEO

**Versi:** 0.2.0  
**Status:** Fitur blog, video pilihan, dan BGM sudah diimplementasikan pada proyek statis. Belum ada media pribadi yang dipasang atau deployment GitHub Pages yang diverifikasi.

## Fitur yang dipertahankan

- Halaman portofolio asli dengan hero, About, Projects, Skills, Photography & Videography, pencapaian, kontak, footer, dan identitas visual CalonCEO.
- Palet warna, token tema, tipografi, animasi reveal, mode gelap/terang, penyimpanan preferensi tema, navigasi mobile, galeri dan lightbox.
- Struktur proyek statis tanpa framework, build step, backend, atau database.
- Kartu proyek dan pencapaian lama tidak diganti dengan klaim baru.

## Penambahan versi 0.2.0

- Bagian **Catatan Perjalanan** diletakkan setelah Projects dan sebelum Skills/Contact. Daftar artikel dan tampilan detail tersedia; isi artikel, tanggal, kategori, ringkasan, sampul, paragraf, subjudul, kutipan, dan daftar disimpan dalam `js/content.js`.
- Navigasi artikel menggunakan hash URL seperti `#journey/slug-artikel`, tombol kembali, serta dukungan riwayat browser.
- Bagian **Video Pilihan** menggunakan elemen HTML5 video dengan `controls`, `playsinline`, dan `preload="metadata"`. URL harus berupa path MP4 lokal atau URL HTTPS langsung yang berakhiran `.mp4`.
- Kontrol **BGM** terpisah dari audio video. Audio memakai `loop` dan `preload="none"`; kontrol awal nonaktif sampai URL MP3 langsung disediakan. BGM tidak autoplay dan kontrol mencakup Play/Pause, status, serta volume.
- Placeholder ditampilkan saat video atau BGM belum dikonfigurasi. Kegagalan pemuatan media akan ditangani tanpa menghapus bagian lain halaman.
- BGM ditempatkan pada alur normal halaman, tidak melayang di atas navigasi, tombol kontak, atau kontrol video.
- README diperbarui dengan petunjuk pengelolaan lewat browser HP Android dan hosting media.

## Konten/aset yang tetap perlu diisi pemilik

- Artikel pribadi yang benar di `js/content.js`.
- URL delivery video MP4 di `featuredVideo.url`, opsional poster.
- URL MP3 di `backgroundMusic.url`, nama musik, dan volume awal.
- Poster lama `images/poster-bijak-bermedsos.jpg` masih belum disertakan; fallback poster yang lama tetap ada.
- Link kontak dan repository publik masih perlu diisi pada `siteConfig.links` di `js/script.js` bila siap.
- Foto dan item Videography tambahan tetap kosong sampai aset asli diberikan.

## Hasil pengujian yang dijalankan

- [x] `node --check js/script.js` — lulus.
- [x] `node --check js/content.js` — lulus.
- [x] Parsing CSS melalui `tinycss2` — 0 parse error.
- [x] Parsing HTML dengan Python `HTMLParser` — berhasil.
- [x] Pemeriksaan ID HTML — tidak ada ID duplikat.
- [x] Pemeriksaan tautan anchor — tidak ada target `#...` yang hilang.
- [x] Referensi file CSS/JS yang ditautkan dari HTML — semuanya ada.
- [x] Elemen gambar pada HTML — atribut `alt` tersedia.
- [x] Uji runtime Chromium/Playwright dengan HTML, CSS, dan JS proyek yang dimuat dalam DOM uji — tidak ditemukan `pageerror` pada skenario yang dijalankan.
- [x] Uji daftar artikel, membuka isi artikel, dan kembali ke daftar menggunakan konten artikel uji — lulus.
- [x] Uji state bawaan: daftar blog kosong menampilkan empty state, video menunjukkan placeholder, BGM nonaktif saat URL kosong — lulus.
- [x] Uji sumber video MP4 uji: metadata 320×180 berhasil dibaca, `controls`, `playsinline`, `preload="metadata"`, serta play/pause tersedia — lulus dengan file uji, bukan video Cloudinary milik pengguna.
- [x] Uji audio uji: BGM dalam keadaan pause sebelum klik, Play/Pause berfungsi, slider volume mengubah volume — lulus dengan rute media uji, bukan URL MP3 produksi.
- [x] Pemeriksaan horizontal overflow pada viewport mobile 390 px dan desktop 1280 px di sesi uji — tidak ditemukan.
- [x] Screenshot pemeriksaan tampilan dibuat dari DOM uji pada layar mobile; identitas visual lama terlihat tetap konsisten.
- [ ] Menguji URL Cloudinary/MP3 sebenarnya — belum dilakukan karena URL/media belum diberikan.
- [ ] Menguji deployment publik GitHub Pages, custom domain, aksesibilitas lintas browser, Lighthouse, dan perangkat Android nyata — belum dilakukan.

**Catatan pengujian browser:** sesi runtime menguji dokumen dan logika proyek dalam DOM Chromium, memakai file MP4/WAV kecil untuk media uji. Pengujian ini tidak membuktikan URL media eksternal atau website publik sudah bekerja. Percobaan navigasi browser ke file lokal/localhost dibatasi oleh lingkungan uji; deployment sebenarnya belum diuji.

## File yang berubah atau ditambahkan

- `index.html` — link navigasi, bagian Catatan Perjalanan, Video Pilihan, serta kontrol BGM.
- `css/style.css` — gaya baru yang mengikuti tema desain dan aturan responsif.
- `js/script.js` — render artikel, routing hash, penanganan video, kontrol BGM, serta validasi URL media.
- `js/content.js` — **file baru** untuk data artikel dan konfigurasi video/BGM.
- `audio/README.md` — **file baru** panduan MP3 lokal.
- `videos/README.md` — diperbarui untuk video MP4 dan hosting eksternal.
- `README.md` — diperbarui dengan langkah kerja mobile, Cloudinary, GitHub Pages, dan troubleshooting.
- `CHANGELOG.md` — entri versi 0.2.0.

## Checklist berikutnya

1. Tambahkan artikel pribadi (atau biarkan blog kosong sampai siap).
2. Upload video ke Cloudinary, tempel URL `.mp4` langsung, lalu uji lewat URL GitHub Pages.
3. Tambahkan MP3 milik sendiri/berlisensi, tempel URL langsung, dan pastikan musik baru berjalan saat tombol ditekan.
4. Pastikan poster gambar asli sudah tersedia jika ingin mengaktifkan pratinjau poster lama.
5. Periksa lagi tampilan di Android setelah GitHub Pages selesai deploy.
