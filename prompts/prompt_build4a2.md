Semua balasan kepada saya dalam bahasa Indonesia.
Waktu sekarang (WIB): [ISI: hari, tanggal, jam WIB]

# BUILD 4a-2 — PantauUsaha AI (butir 6-8)

Lampiran: PantauUsaha_Papan_v4a1.html (hasil 4a-1 yang sudah saya periksa)

## ATURAN KERJA (wajib)
1. JANGAN menulis tes, JANGAN menjalankan tes, JANGAN membuka browser untuk menguji. Saya menguji sendiri di luar WorkBuddy.
2. CARA KERJA HEMAT KREDIT: salin berkas sumber menjadi PantauUsaha_Papan_v4.html, lalu ubah dengan EDIT TERARAH pada fungsi/bagian yang terkait saja. JANGAN menulis ulang seluruh berkas. Baca berkas sumber SEKALI, cari bagian yang perlu diubah (cari nama fungsi), lalu langsung edit. Tidak perlu berpikir panjang atau memetakan seluruh berkas.
3. Berkas sumber (PantauUsaha_Papan_v4a1.html) JANGAN diubah.
4. Satu berkas HTML, tanpa server, data mock saja (localStorage key tetap pantauusaha_papan_v1; data lama harus tetap terbaca).
5. Kerjakan HANYA butir di bawah. Jangan menambah fitur lain, jangan merombak gaya tampilan.
6. Satu kali kerja, tidak ada putaran perbaikan sendiri. Butir yang meragukan: kerjakan yang jelas, tulis sisanya di "Butir tidak dikerjakan / ragu".
7. Bila sudah ada hasil sebagian, SIMPAN berkas keluaran lebih dulu, lalu lanjut butir berikutnya (supaya hasil tidak hilang bila saya menghentikan).
8. Di akhir, tulis ringkasan per butir: DIKERJAKAN / SEBAGIAN / TIDAK, dengan nama fungsi yang diubah. Jangan menulis "selesai semua" tanpa rincian.

## BUTIR 6 — Rencana vs Realisasi (Pengawas)
- Filter rentang tanggal (dari-sampai), bawaan kemarin sampai hari ini (WIB). Pakai komponen rentang tanggal yang sama bisa dipakai ulang (akan dipakai Report di 4b).
- Filter status, bawaan: MENUNGGU TINJAUAN + MENUNGGU KONFIRMASI PENGAWAS.
- Kotak centang per laporan + "Setuju (n terpilih)" untuk persetujuan lebih dari satu. Laporan Lembur dan Di luar rencana TIDAK ikut persetujuan massal: kotaknya nonaktif, disetujui satu per satu.
- Tidak setuju: tetap satu per satu, alasan wajib.
- Audit Log: satu baris per laporan, juga untuk persetujuan massal (jangan satu baris untuk banyak laporan).
- Bila Pengawas yang menginput atas nama Mandor juga yang menyetujui, aplikasi menulis catatan otomatis "diinput dan disetujui oleh orang yang sama" (hanya dalam kasus itu).
- Baris rencana tanpa laporan tampil sebagai "Belum dilaporkan" (hanya Pengawas).

## BUTIR 7 — Jembatan agen (tab Agen, Pengawas)
Perintah yang disalin harus otomatis berisi, berurutan:
a. Baris PERTAMA, kalimat persis ini tanpa diubah: "Semua balasan kepada saya dalam bahasa Indonesia." (wajib ada di SETIAP perintah yang disalin ke WorkBuddy: perintah satu laporan, perintah banyak laporan, dan perintah dari tab Agen; tidak boleh ada jalur salin yang melewatkannya; tidak bisa dihapus pengguna dari aplikasi). Lalu "Waktu sekarang (WIB): ..." dari jam aplikasi.
b. Blok "DATA MASTER ZONA" (dari Master Data).
c. Blok "RENCANA HARI INI" (semua rencana tanggal terkait, termasuk yang belum dilaporkan).
d. Laporan yang ditinjau, dengan label "Area" dan "Zona", dan "Alasan Pengawas" bila ada.
e. CARA MENJAWAB: contoh baris pakai ID FIKTIF (jelas bukan ID asli) — satu baris per laporan: `ID laporan | Tanda | catatan | ID rencana`. Hapus teks "(ID rencana dikosongkan di jawaban)".
Pembaca jawaban ("Baca hasil dari teks"):
- Terima 5 Tanda: Sesuai, Tidak sesuai, Di luar rencana, Perlu konfirmasi, Belum dilaporkan. Tanda lain = ditolak/ditandai merah di pratinjau.
- Baris "Belum dilaporkan" memakai ID laporan "-"; tampilkan terkelompok per Mandor/Area di tab Agen dan di Rencana vs Realisasi.
- Bila teks diubah setelah "Baca", wajib baca ulang sebelum "Simpan hasil agen" (tolak simpan bila berbeda).
- Awalan di catatan seperti [Lembur], [Terlambat], [Lewat batas], [Kurang data], [Perlu pengajuan], [Hari libur], [Salat Jumat] tampil sebagai lencana.
- Hapus tombol & kotak tempel "Teruskan catatan ke Mandor" (fitur dibuang).
- Excel unduhan: tambah kolom ke-11 "Catatan agen"; tambah pintasan "Unduh Excel" di Rencana vs Realisasi.

## BUTIR 8 — Perbaikan kecil dari pemeriksaan v4a1 (hanya teks/nama, JANGAN ubah logika)
a. Nama lembar Excel unduhan Rencana vs Realisasi: ganti "Rencana vs Realisasi-Rencana" dan "Rencana vs Realisasi-Realisasi" menjadi cukup "Rencana" dan "Realisasi". Nama berkas tetap "Rencana_vs_Realisasi_<tanggal>.xlsx" / ".csv".
b. Teks ritase Driver: di mana pun tertulis "DITOLAK, maksimal 7" atau "ritase ke-8 ditolak" (teks tampilan, bukan komentar kode), ganti menjadi "Perlu pengajuan terpisah (lebih dari 7 ritase)". Perilaku tombol/validasi TIDAK diubah; hanya kalimatnya. Selaraskan juga kalimat yang sama di perintah ke agen.

Mulai kerjakan sekarang.
