Semua balasan kepada saya dalam bahasa Indonesia.
Waktu sekarang (WIB): [ISI: hari, tanggal, jam WIB]

# BUILD 4b-1 — Menu Report: periode, angka acuan, perintah ke agen (v4 -> v5a)

Lampiran: PantauUsaha_Papan_v4.html (hasil yang sudah saya periksa)

## ATURAN KERJA (wajib)
1. JANGAN menulis tes, JANGAN menjalankan tes, JANGAN membuka browser untuk menguji. Saya menguji sendiri di luar WorkBuddy.
2. CARA KERJA HEMAT KREDIT: salin berkas sumber menjadi PantauUsaha_Papan_v5a.html, lalu ubah dengan EDIT TERARAH. JANGAN menulis ulang seluruh berkas. Baca berkas sumber SEKALI, cari bagian terkait (nama fungsi), lalu langsung edit. Tidak perlu memetakan seluruh berkas.
3. Berkas sumber (PantauUsaha_Papan_v4.html) JANGAN diubah.
4. Satu berkas HTML, tanpa server, data mock saja (localStorage key tetap pantauusaha_papan_v1; data lama harus tetap terbaca). Tanpa pustaka luar.
5. Kerjakan HANYA butir di bawah. Menu dan fitur lain jangan diubah.
6. Agen dan aplikasi TIDAK PERNAH menghitung gaji (di luar cakupan).
7. Satu kali kerja, tidak ada putaran perbaikan sendiri. Butir yang meragukan: kerjakan yang jelas, tulis sisanya di "Butir tidak dikerjakan / ragu".
8. SIMPAN berkas keluaran lebih dulu setelah bagian pertama selesai, lalu lanjut (supaya hasil tidak hilang bila saya menghentikan).
9. Di akhir, ringkasan per butir: DIKERJAKAN / SEBAGIAN / TIDAK, dengan nama fungsi yang diubah. Jangan menulis "selesai semua" tanpa rincian.

## BUTIR 1 — Menu "Report"
Tambahkan menu "Report" HANYA untuk Pengawas dan Admin (peran lain tidak melihatnya). Letakkan sebelum Audit Log.

## BUTIR 2 — Pilih periode dan jenis report
- Periode: Mingguan (Sabtu-Jumat yang memuat tanggal dipilih), Bulanan (tanggal 1 sampai akhir bulan), atau rentang bebas memakai komponen rentang tanggal yang sudah ada di v4 (komponenRentangTanggal / bacaRentangTanggal).
- Jenis report: (a) "Matriks klien" (b) "Rekap penggajian" (Sabtu-Jumat).

## BUTIR 3 — Angka acuan dari aplikasi
Hitung HANYA dari laporan berstatus CLOSED dalam periode: per orang = hari kerja, ritase (Driver), hari Lembur; per tanggal = kegiatan rencana vs realisasi. Laporan belum CLOSED dicatat sebagai BELUM FINAL (tidak dihitung). Tampilkan tabel angka acuan di layar.

## BUTIR 4 — Perintah ke agen
Tombol "Salin perintah ke agen" (memakai fungsi salin yang sudah ada, supaya kalimat wajib tetap di baris pertama). Isi paket berurutan: baris PERTAMA persis "Semua balasan kepada saya dalam bahasa Indonesia." lalu "Waktu sekarang (WIB): ...", jenis dan periode report, data mentah laporan CLOSED periode itu, daftar BELUM FINAL, angka acuan aplikasi, hari libur/Jumat bila ada di data, lalu instruksi: hitung ulang dari data mentah, bandingkan dengan angka acuan, tandai SELISIH, laporan susulan, hari libur, anomali; tulis CATATAN KLIEN; jangan menghitung gaji. Sertakan format jawaban di bawah beserta contoh baris ber-ID FIKTIF.

## FORMAT JAWABAN AGEN (parser persis ini; satu baris per item, pemisah " | ")
REKAP | periode | nama | peran | hari kerja | ritase | hari Lembur | hari libur | catatan
MATRIKS | tanggal | kegiatan | orang | rencana | realisasi | catatan
BELUM FINAL | ID laporan | alasan
SELISIH | item | angka agen | angka acuan | catatan
CATATAN KLIEN | paragraf
Lalu satu baris sumber global di akhir. Baris dengan kata kunci lain = ditandai merah di pratinjau, tidak dipakai.

TAHAP INI belum memproses jawaban agen (itu 4b-2). Cukup sampai paket perintah dan tabel angka acuan.

Mulai kerjakan sekarang.
