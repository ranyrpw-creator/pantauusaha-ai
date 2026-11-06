Semua balasan kepada saya dalam bahasa Indonesia.
Waktu sekarang (WIB): [ISI: hari, tanggal, jam WIB]

# BUILD 4b — Menu Report (lanjutan dari PantauUsaha_Papan_v4.html)

Lampiran: PantauUsaha_Papan_v4.html (hasil build 4a yang SUDAH saya periksa).

## ATURAN KERJA (wajib)
1. JANGAN menulis atau menjalankan tes apa pun di WorkBuddy.
2. Hasilkan berkas BARU: PantauUsaha_Papan_v5.html. v4 JANGAN diubah.
3. Hanya menambah menu Report; tidak mengubah menu/fitur lain.
4. Hemat kredit: salin v4 menjadi v5 lalu TAMBAHKAN menu Report dengan edit terarah, JANGAN menulis ulang seluruh berkas; baca sekali, simpan hasil sebagian lebih dulu. Satu kali tulis. Akhiri dengan ringkasan DIKERJAKAN/SEBAGIAN/TIDAK + daftar yang ragu.
5. Data mock saja. Agen TIDAK PERNAH menghitung gaji; aplikasi juga tidak (di luar cakupan).

## MENU REPORT
Peran: Pengawas dan Admin (menu "Report"). Peran lain tidak melihatnya.
Alur 5 langkah:
1. Pilih periode (mingguan: Sabtu-Jumat; bulanan: 1 s/d akhir bulan; atau rentang bebas dengan komponen rentang tanggal dari 4a) dan jenis report: (a) "Matriks klien" atau (b) "Rekap penggajian" (Sabtu-Jumat).
2. Aplikasi menghitung ANGKA ACUAN hanya dari laporan berstatus CLOSED (disetujui). Tampilkan: hari kerja, ritase, hari Lembur per orang; kegiatan per tanggal. Laporan belum CLOSED dicatat sebagai BELUM FINAL (tidak dihitung).
3. Tombol "Salin perintah ke agen": paket diawali baris PERTAMA persis: "Semua balasan kepada saya dalam bahasa Indonesia." lalu "Waktu sekarang (WIB): ...", data mentah laporan CLOSED periode itu, daftar BELUM FINAL, angka acuan aplikasi, hari libur/Jumat bila ada di data, dan format jawaban di bawah. Instruksi ke agen: hitung ulang dari data mentah, bandingkan dengan angka acuan, tandai SELISIH, laporan susulan, hari libur, anomali; tulis CATATAN KLIEN; jangan menghitung gaji.
4. Kotak tempel jawaban agen -> "Baca hasil" (pratinjau, baca ulang bila teks berubah) -> tampilkan perbandingan angka agen vs acuan dengan SELISIH berwarna.
5. Pengawas/Admin memeriksa lalu "Setujui report" (wajib centang "sudah saya periksa") -> tombol Unduh Excel aktif; Audit Log mencatat satu baris (siapa, periode, jenis, jumlah SELISIH). Tanpa persetujuan tidak ada unduhan.

## FORMAT JAWABAN AGEN (parser harus persis ini; satu baris per item, pemisah " | ")
REKAP | periode | nama | peran | hari kerja | ritase | hari Lembur | hari libur | catatan
MATRIKS | tanggal | kegiatan | orang | rencana | realisasi | catatan
BELUM FINAL | ID laporan | alasan
SELISIH | item | angka agen | angka acuan | catatan
CATATAN KLIEN | paragraf
Lalu satu baris sumber global di akhir. Baris dengan kata kunci lain = ditandai merah di pratinjau, tidak dipakai.

## EXCEL
- Matriks klien: satu lembar, 31 kolom tanggal; baris Rencana berlatar kuning; tanggal tidak valid (mis. 31 di bulan 30 hari) abu-abu; kolom "Total Aktivitas"; CATATAN KLIEN di bawah.
- Rekap penggajian: 3 lembar (Rekap per orang, Rincian per tanggal, Catatan & selisih). Tanpa kolom gaji/rupiah.
- Gunakan penulis XLSX yang sudah ada di aplikasi (tanpa pustaka luar); tambahkan gaya (fill kuning/abu, tebal) di styles.xml.

Mulai kerjakan sekarang.
