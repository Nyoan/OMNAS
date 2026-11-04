# OMNAS Smart Prep 3.0 — siap untuk GitHub Pages

Aplikasi belajar berbasis browser dengan 102 latihan (54 soal dari PDF OMNAS 15 yang diberikan pengguna, 36 soal tambahan, dan 12 uraian), pembahasan teks, serta tiga papan tulis interaktif. **Tidak berafiliasi dengan penyelenggara OMNAS.**

**Mulai dari sini:** baca [DEPLOY_GITHUB.md](DEPLOY_GITHUB.md) untuk cara mengunggah dan menerbitkan.

## Struktur folder

```text
index.html                  # Halaman utama; harus berada di root repository
.nojekyll                   # Agar GitHub Pages menerbitkan situs apa adanya
data/bank-soal.json         # Salinan data bank soal untuk pengembangan
data/template-pembahasan-video.json           # Templat konten untuk pengembangan
README.md
DEPLOY_GITHUB.md
FRAMEWORK.md
```

File `index.html` sudah memuat bank soal dan gambar sehingga aplikasi berjalan tanpa harus mengambil `data/bank-soal.json` melalui jaringan. Tidak ada backend atau build step. Bisa dihosting sebagai static site.

## Batasan penting

- Hasil belajar dua anak disimpan di `localStorage` pada browser/perangkat masing-masing. Pindah HP atau hapus data browser dapat menyebabkan hilangnya riwayat. Gunakan ekspor CSV untuk menyimpan cadangan.
- Tidak ada login, server database, ataupun sinkronisasi hasil antarperangkat.
- Tidak ada video MP4 dengan narasi manusia yang terintegrasi dalam paket ini. Tiga pembahasan papan tulis tersedia; rekaman suara manusia hanya dapat dipilih sebagai berkas lokal pada antarmuka papan tulis (sinkronisasi langkah masih manual).
- Situs di GitHub Pages dapat dilihat publik. Sebelum menerbitkan, **periksa izin publikasi ulang soal-soal OMNAS yang berasal dari PDF pihak ketiga**. Jangan memasukkan nama anak, alamat, laporan pribadi, maupun data sensitif dalam repository.
- Jangan menganggap kata 'source' pada soal tambahan sebagai izin untuk menyalin konten milik pihak ketiga. Soal tambahan dibuat baru dan tidak resmi.

Tidak ada lisensi redistribusi materi pihak ketiga yang diberikan oleh paket ini.
