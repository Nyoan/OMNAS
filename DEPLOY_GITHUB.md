# Cara Deploy OMNAS Smart Prep 3.0 ke GitHub Pages

**Persyaratan:** akun GitHub. Pada paket gratis, gunakan repository **Public** untuk GitHub Pages. Ingat: situs yang diterbitkan di GitHub Pages tersedia publik, termasuk jika repository privat pada paket yang mengizinkannya.

## Cara termudah (tanpa command line)

1. Masuk ke https://github.com dan buka https://github.com/new.
2. Buat repository bernama `omnas-smart-prep` (nama ini contoh, bebas diganti). Pada akun GitHub Free, pilih `Public` agar GitHub Pages bisa dipakai. Sebelum memilih Public, pastikan Anda berhak menerbitkan bank soal OMNAS yang ada di aplikasi.
3. Klik **Create repository**.
4. Di halaman repository, pilih **Add file** → **Upload files**. **Ekstrak ZIP lebih dahulu** dan unggah isi folder `OMNAS_GitHub_Pages_Ready`, bukan folder induk atau ZIP-nya. Pastikan `index.html` tampil di root repository, sejajar dengan `README.md`.
5. Klik **Commit changes** untuk menyimpan berkas ke branch `main`.
6. Masuk ke **Settings** → **Pages**. Di bagian **Build and deployment**, pilih:
   - **Source:** `Deploy from a branch`
   - **Branch:** `main`
   - **Folder:** `/(root)`
   lalu klik **Save**.
7. Setelah deployment GitHub Pages berhasil, situs akan tersedia di `https://USERNAME.github.io/omnas-smart-prep/` (ganti `USERNAME` dengan username GitHub Anda). GitHub mungkin perlu beberapa menit untuk menampilkan situs.
8. Klik link situs pada **Settings → Pages**, lalu tes **Matematika kelas 4**, **Matematika kelas 5**, dan **Bahasa Inggris kelas 5** di HP.

**Penting:** Nama file utama **harus** `index.html` (huruf kecil) dan diletakkan tepat di root folder publishing. Jangan upload ZIP sebagai satu berkas untuk menjadi situs; ekstrak dan unggah berkas-berkasnya. GitHub web upload terkadang menyembunyikan dotfile, tetapi `.nojekyll` hanya tambahan (bukan syarat mutlak).

## Memperbarui aplikasi

Ubah `index.html` (dan sumber lain bila digunakan) pada repository, lalu commit ke branch `main`. GitHub Pages akan menerbitkan ulang perubahan. Jika mengganti bank soal dalam `data/bank-soal.json` saja, situs **tidak otomatis berubah**, karena bank soal juga ditanam di `index.html` untuk penggunaan offline. Perubahan soal harus diterapkan pada `index.html` juga.

## Jika muncul 404

- Pastikan repository benar, Settings → Pages menunjukkan deployment berhasil, dan `index.html` ada di root repository.
- Pastikan URL memuat **nama repository**, termasuk garis miring terakhir: `https://USERNAME.github.io/omnas-smart-prep/`.
- Periksa **Actions** di GitHub untuk log deployment jika Pages gagal.
- Jika membuka `https://USERNAME.github.io/` saja, itu adalah situs root akun, bukan situs repository ini.

## Privasi dan hak cipta

- GitHub Pages bukan sistem akun siswa; tidak ada login atau penyimpanan nilai di server.
- Hasil lokal pada HP ibu/ayah tidak muncul otomatis di HP anak, dan sebaliknya.
- Konten pihak ketiga yang diambil dari PDF OMNAS tidak otomatis bebas dibagikan secara publik. Dapatkan izin bila diperlukan atau gunakan versi konten yang memang boleh diterbitkan sebelum memilih repository Public.

Panduan resmi GitHub: https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site
