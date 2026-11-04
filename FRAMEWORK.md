# Arsitektur OMNAS Smart Prep 3.0

## 1. Prinsip rancangan

**Satu pengalaman untuk dua anak, dengan kemajuan yang benar-benar terpisah.** Anak mengerjakan terlebih dahulu, kemudian belajar dari kesalahan. Pembahasan harus memperlihatkan *mengapa* suatu langkah dilakukan. Tanpa kertas, tanpa memaksa narasi suara sintetis berkualitas rendah.

### Alur belajar anak

`Pilih anak → Pilih bidang & sumber → Jawab soal → Periksa → Solusi per tahap → Latihan ulang → Riwayat progres`

### Alur orang tua

`Pilih profil → Lihat akurasi & materi lemah → Unduh laporan CSV → Pilihkan sesi remedial`

## 2. Modul produk

| Modul | Fungsi | Kondisi dalam prototipe |
|---|---|---|
| Profil dua anak | Memisahkan akses materi dan riwayat | Tersedia lokal |
| Bank soal | OMNAS 15 + latihan tambahan; nomor dan halaman asal | 102 soal tersedia |
| Mesin latihan | Pilihan ganda, uraian, campuran 10 soal, penilaian | Tersedia |
| Penjelasan tekstual | Kunci jawaban, alasan, cara mengerjakan | 102 soal tersedia |
| Papan tulis | Satu tahap per layar, kontrol maju/mundur | 3 soal tersedia |
| Narasi manusia | Rekaman suara natural, dapat diunduh offline | Input file audio manual saja, tidak ada rekaman bawaan |
| Dashboard orang tua | Akurasi, kesalahan per topik, ekspor CSV | Tersedia lokal |
| Video produksi | MP4 narasi sinkron, subtitle, kontrol ulang | **Belum diproduksi dalam versi ini** |
| Sinkronisasi cloud | Hasil di beberapa perangkat | Belum tersedia |

## 3. Struktur data soal

Setiap soal memiliki kunci unik (`id`) seperti `m2-omnas-11`, `m3-omnas-7`, dan `e3-omnas-9`.

```
{
  "id": "m2-omnas-11",
  "origin": "omnas",
  "no": 11,
  "page": 3,
  "topic": "KPK",
  "q": "...",
  "options": ["A", "B", "C", "D"],
  "answer": 2,
  "why": "Langkah solusi...",
  "difficulty": 2,
  "image": null
}
```

`answer` memakai indeks 0 sampai 3; nomor soal asli berbeda dengan indeks. `origin='new'` menunjukkan soal yang disusun baru dan perlu disertai keterangan referensi inspirasi, bukan klaim berasal dari sumber resmi. Soal uraian tidak diberi skor otomatis.

## 4. Framework pembahasan video baru

**Format baku per soal**

1. *Pancingan soal (5–15 detik)* — baca inti soal, tandai informasi penting.
2. *Alasan memilih strategi (15–30 detik)* — misalnya mengapa KPK, bukan FPB.
3. *Perhitungan atau penalaran bertahap (30–60 detik)* — animasi mengikuti penjelasan, hanya satu ide per layar.
4. *Cek jawaban dan jebakan umum (15–30 detik)* — pastikan satuan/operasi/grammar benar.
5. *Transfer strategi (15–30 detik)* — contoh variasi cepat agar anak memahami, bukan meniru.

Target durasi 90–180 detik per soal, tetapi mengikuti tingkat kesulitan. Anak kelas 4 mendapat ilustrasi konkret dan laju lebih lambat. Matematika kelas 5 memperkenalkan cara cek cepat. Bahasa Inggris memakai penjelasan bilingual dengan contoh pronunciation yang benar.

**Standar audio:** narasi manusia yang jelas dan ekspresif; rekaman asli atau layanan suara natural yang secara subjektif lolos penilaian keluarga. Jangan produksi masal sebelum sampel disetujui. Hindari pengucapan huruf/angka seperti robot; bahasa Inggris diperiksa pelafalannya. Sertakan transkrip, subtitle dan tombol mute. Materi harus tetap dipahami saat video tanpa audio.

**Standar visual:** resolusi master 1920×1080 (16:9), huruf terbaca di layar HP, subtitle tidak menutup operasi matematika, setiap animasi sinkron dengan kalimat. Warna dipakai untuk membedakan data–proses–jawaban, bukan hiasan semata.

**Struktur folder produksi ketika narasi/video tersedia:**

```
assets/
  lessons/
    m2-omnas-11/
      script.md          # naskah guru
      voice-human.wav    # suara disetujui
      storyboard.json    # visual per adegan
      subtitle.srt       # subtitle
      master.mp4         # video final
```

Metadata kontrol kualitas per video ada di `data/template-pembahasan-video.json`.

## 5. Quality gates sebelum setiap video diterbitkan

- **Gate A, naskah asli:** nomor, level, dan halaman sama dengan file sumber; gambar diperiksa secara visual.
- **Gate B, solusi:** seluruh perhitungan/kunci jawaban diverifikasi manual; soal ambigu atau kunci keliru ditandai dan tidak dijadikan evaluasi otomatis.
- **Gate C, pedagogi:** guru/editor dapat menjelaskan mengapa setiap langkah dilakukan; ada kesalahan umum yang dibahas.
- **Gate D, suara:** tidak robotik; istilah matematika dan bahasa Inggris dilafalkan benar; cocok untuk anak kelas 4–5.
- **Gate E, final:** timing audio, animasi, dan subtitle sesuai; uji tampilan HP dan laptop; tombol putar/pause/ulang bekerja.

## 6. Rencana pengembangan bertahap

**Tahap sekarang (v3 prototipe):** satu file HTML offline, 102 soal dan solusi teks, tiga papan tulis interaktif, dua profil, dashboard dan ekspor CSV.

**Tahap produksi narasi:** produksi dan setujui narasi manusia pada tiga soal contoh, ganti audio manual dengan player HTML5 yang terhubung ke file audio/video final. Pastikan browser dapat tetap memutar dengan subtitle saat audio dimatikan.

**Tahap pengayaan pembahasan:** perluas storyboard/video hanya setelah standar A–E stabil; prioritaskan soal yang sering dijawab salah. Tambahkan remedial otomatis per topik.

**Tahap pengayaan bank soal (fase 2):** tingkatkan soal ke 300–500 per bidang dengan sumber jelas, validasi editorial, dan pelacakan progres tingkat topik. Fase ini terpisah dari penyempurnaan kualitas pembahasan.

## 7. Batasan teknis dan ruang lingkup

Prototipe ini tidak mempunyai backend, integrasi YouTube, pengisi suara natural otomatis, editor konten bawaan, atau hosting publik. Penyimpanan dan pilihan audio berlangsung lokal; data tidak tersinkron otomatis. Framework sudah memisahkan ID soal–pembahasan agar nanti file MP4 per soal dapat dihubungkan tanpa mengganti seluruh bank soal.
