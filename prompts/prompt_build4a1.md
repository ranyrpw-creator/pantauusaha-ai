Semua balasan kepada saya dalam bahasa Indonesia.
Waktu sekarang (WIB): [ISI: hari, tanggal, jam WIB]

# BUILD 4a-1 — PantauUsaha AI (butir 1-5)

Lampiran: PantauUsaha_Papan_v3.html

## ATURAN KERJA (wajib)
1. JANGAN menulis tes, JANGAN menjalankan tes, JANGAN membuka browser untuk menguji. Saya menguji sendiri di luar WorkBuddy.
2. CARA KERJA HEMAT KREDIT: salin berkas sumber menjadi PantauUsaha_Papan_v4a1.html, lalu ubah dengan EDIT TERARAH pada fungsi/bagian yang terkait saja. JANGAN menulis ulang seluruh berkas. Baca berkas sumber SEKALI, cari bagian yang perlu diubah (cari nama fungsi), lalu langsung edit. Tidak perlu berpikir panjang atau memetakan seluruh berkas.
3. Berkas sumber (PantauUsaha_Papan_v3.html) JANGAN diubah.
4. Satu berkas HTML, tanpa server, data mock saja (localStorage key tetap pantauusaha_papan_v1; data lama harus tetap terbaca).
5. Kerjakan HANYA butir di bawah. Jangan menambah fitur lain, jangan merombak gaya tampilan.
6. Satu kali kerja, tidak ada putaran perbaikan sendiri. Butir yang meragukan: kerjakan yang jelas, tulis sisanya di "Butir tidak dikerjakan / ragu".
7. Bila sudah ada hasil sebagian, SIMPAN berkas keluaran lebih dulu, lalu lanjut butir berikutnya (supaya hasil tidak hilang bila saya menghentikan).
8. Di akhir, tulis ringkasan per butir: DIKERJAKAN / SEBAGIAN / TIDAK, dengan nama fungsi yang diubah. Jangan menulis "selesai semua" tanpa rincian.

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

Mulai kerjakan sekarang.
