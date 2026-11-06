Semua balasan kepada saya dalam bahasa Indonesia.
Waktu sekarang (WIB): [ISI: hari, tanggal, jam WIB]

# BUILD 4a — PantauUsaha AI (lanjutan dari v3)

Lampiran: PantauUsaha_Papan_v3.html (dan Dokumen Rancang BRD/FSD/TSD bila terlampir).

## ATURAN KERJA (wajib)
1. JANGAN menulis tes, JANGAN menjalankan tes, JANGAN membuka browser untuk menguji. Saya menguji sendiri di luar WorkBuddy.
2. Hasilkan berkas BARU: PantauUsaha_Papan_v4.html. Berkas v3 JANGAN diubah.
3. Satu berkas HTML, tanpa server, data mock saja (localStorage key tetap pantauusaha_papan_v1; format data lama harus tetap terbaca).
4. Kerjakan HANYA butir 1-7 di bawah. Jangan menambah fitur lain, jangan merombak gaya tampilan. Menu Report BUKAN bagian ini (itu build 4b).
5. Hemat kredit: satu kali tulis, tidak ada putaran perbaikan sendiri. Bila ada butir yang meragukan, kerjakan yang jelas, lalu tulis di akhir daftar "Butir tidak dikerjakan / ragu" apa adanya.
6. Di akhir, tulis ringkasan per butir: DIKERJAKAN / SEBAGIAN / TIDAK, dengan nama fungsi yang diubah. Jangan menulis "selesai semua" tanpa rincian.

## BUTIR 1 — Menu per peran
- Mandor & Driver: hapus tab "Agen". Menu: Rencana Saya, Lapor, Riwayat.
- Pemilik: Rencana Mingguan, Laporan, Rencana vs Realisasi, Riwayat, Audit Log.
- Pengawas: tidak berubah selain nama butir 2 (Rencana Mingguan, Lapor, Agen, Rencana vs Realisasi, Riwayat, Master Data, Audit Log).
- Admin: Rencana Mingguan, Laporan, Rencana vs Realisasi (hanya lihat), Master Data, Audit Log. (Menu Report ditambah di build 4b.)

## BUTIR 2 — Ganti nama
"Plan vs Realisasi" -> "Rencana vs Realisasi" di SEMUA tempat: menu, judul halaman, teks bantuan, nama berkas Excel unduhan, judul lembar. Cari semua kemunculan, jangan hanya menu.

## BUTIR 3 — Tab Lapor (Mandor/Driver)
- Tampilkan laporan milik sendiri beserta status.
- Laporan berstatus DIKEMBALIKAN KE AGEN / dikembalikan Pengawas: tampilkan "Catatan Pengawas" dan tombol "Perbaiki laporan ini". Tombol itu memperbarui laporan YANG SAMA (ID laporan tetap, status kembali MENUNGGU AGEN), bukan membuat laporan baru. Setelah ditekan, halaman otomatis scroll ke formulir perbaikan.
- Badge pada menu: "Lapor (n)" = jumlah laporan dikembalikan.

## BUTIR 4 — Dropdown Lapor
Kegiatan rencana yang sudah dilaporkan: tampil abu-abu/nonaktif, KECUALI yang dikembalikan (tetap bisa dipilih). Bila ada laporan dikembalikan, tampilkan peringatan "Ada laporan dikembalikan — gunakan Perbaiki, bukan lapor baru" supaya tidak ada laporan ganda.

## BUTIR 5 — Rencana Saya (Mandor/Driver)
- Pilihan "Hari ini" / "Minggu ini" (Minggu ini = periode Sabtu-Jumat yang memuat hari ini).
- Kolom Status per baris: Belum dilaporkan / Menunggu / Disetujui / Dikembalikan; tombol "Lapor" (belum dilaporkan) atau "Perbaiki" (dikembalikan) langsung di baris.
- Label: "(ke-N)" -> "No. rencana N"; kolom "KE" -> "No."; Driver: "ritase ke-N dari 4" -> "Ritase ke-N (normal 1-4, lembur 5-7)".

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

Mulai kerjakan sekarang.
