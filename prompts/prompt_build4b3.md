Semua balasan kepada saya dalam bahasa Indonesia.
Waktu sekarang (WIB): [ISI: hari, tanggal, jam WIB]

# BUILD 4b-3 — Menu Report: HANYA unduhan Excel (v5 -> v6)

Lampiran: PantauUsaha_Papan_v5.html (hasil 4b-2 yang sudah saya periksa)

## ATURAN KERJA (wajib)
1. JANGAN menulis tes, JANGAN menjalankan tes, JANGAN membuka browser untuk menguji. Saya menguji sendiri di luar WorkBuddy.
2. CARA KERJA HEMAT KREDIT: salin berkas sumber menjadi PantauUsaha_Papan_v6.html, lalu ubah dengan EDIT TERARAH. JANGAN menulis ulang seluruh berkas. Baca berkas sumber SEKALI, cari bagian terkait (nama fungsi), lalu langsung edit. Tidak perlu memetakan seluruh berkas.
3. Berkas sumber (PantauUsaha_Papan_v5.html) JANGAN diubah.
4. Satu berkas HTML, tanpa server, data mock saja (localStorage key tetap pantauusaha_papan_v1; data lama harus tetap terbaca). Tanpa pustaka luar.
5. Kerjakan HANYA butir di bawah. Menu dan fitur lain jangan diubah.
6. Agen dan aplikasi TIDAK PERNAH menghitung gaji (di luar cakupan).
7. Satu kali kerja, tidak ada putaran perbaikan sendiri. Butir yang meragukan: kerjakan yang jelas, tulis sisanya di "Butir tidak dikerjakan / ragu".
8. SIMPAN berkas keluaran lebih dulu setelah bagian pertama selesai, lalu lanjut (supaya hasil tidak hilang bila saya menghentikan).
9. Di akhir, ringkasan per butir: DIKERJAKAN / SEBAGIAN / TIDAK, dengan nama fungsi yang diubah. Jangan menulis "selesai semua" tanpa rincian.

## KONTEKS
Menu Report sudah punya periode, angka acuan, perintah ke agen, pembaca jawaban agen, dan persetujuan (4b-1 dan 4b-2). Tahap ini HANYA menambah pembuatan berkas Excel dari data hasil baca jawaban agen yang sudah disetujui. Jangan mengubah bagian lain.

## BUTIR 1 — Tombol "Unduh Excel" (aktif hanya setelah "Setujui report")
Pakai penulis XLSX yang sudah ada di aplikasi (fungsi unduhXlsx); tambahkan gaya (fill kuning/abu, tebal) di styles.xml bila perlu. Tanpa pustaka luar.
- Jenis "Matriks klien": SATU lembar, 31 kolom tanggal; baris Rencana berlatar kuning; tanggal tidak valid (mis. 31 di bulan 30 hari) berlatar abu-abu; kolom "Total Aktivitas"; CATATAN KLIEN di bawah tabel.
- Jenis "Rekap penggajian": 3 lembar bernama "Rekap per orang", "Rincian per tanggal", "Catatan & selisih". TANPA kolom gaji/rupiah.
- Nama berkas: Report_<jenis>_<tanggal awal>_<tanggal akhir>.xlsx.
- Audit Log mencatat satu baris saat berkas diunduh (siapa, periode, jenis).

Mulai kerjakan sekarang.
