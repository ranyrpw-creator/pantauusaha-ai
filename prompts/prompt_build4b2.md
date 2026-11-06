Semua balasan kepada saya dalam bahasa Indonesia.
Waktu sekarang (WIB): [ISI: hari, tanggal, jam WIB]

# BUILD 4b-2 — Menu Report: baca jawaban agen, Excel, persetujuan (v5a -> v5)

Lampiran: PantauUsaha_Papan_v5a.html (hasil 4b-1 yang sudah saya periksa)

## ATURAN KERJA (wajib)
1. JANGAN menulis tes, JANGAN menjalankan tes, JANGAN membuka browser untuk menguji. Saya menguji sendiri di luar WorkBuddy.
2. CARA KERJA HEMAT KREDIT: salin berkas sumber menjadi PantauUsaha_Papan_v5.html, lalu ubah dengan EDIT TERARAH. JANGAN menulis ulang seluruh berkas. Baca berkas sumber SEKALI, cari bagian terkait (nama fungsi), lalu langsung edit. Tidak perlu memetakan seluruh berkas.
3. Berkas sumber (PantauUsaha_Papan_v5a.html) JANGAN diubah.
4. Satu berkas HTML, tanpa server, data mock saja (localStorage key tetap pantauusaha_papan_v1; data lama harus tetap terbaca). Tanpa pustaka luar.
5. Kerjakan HANYA butir di bawah. Menu dan fitur lain jangan diubah.
6. Agen dan aplikasi TIDAK PERNAH menghitung gaji (di luar cakupan).
7. Satu kali kerja, tidak ada putaran perbaikan sendiri. Butir yang meragukan: kerjakan yang jelas, tulis sisanya di "Butir tidak dikerjakan / ragu".
8. SIMPAN berkas keluaran lebih dulu setelah bagian pertama selesai, lalu lanjut (supaya hasil tidak hilang bila saya menghentikan).
9. Di akhir, ringkasan per butir: DIKERJAKAN / SEBAGIAN / TIDAK, dengan nama fungsi yang diubah. Jangan menulis "selesai semua" tanpa rincian.

## KONTEKS
Menu Report sudah ada (4b-1): periode, jenis report, angka acuan, dan tombol salin perintah. Tahap ini melengkapi sisi jawaban.

## BUTIR 0 — Perbaikan dari pemeriksaan v5a (kerjakan PERTAMA, kecil)
a. HITUNG HARI LEMBUR MANDOR (kekeliruan): fungsi adaLemburReport / hitungAngkaAcuan sekarang hanya melihat data laporan, sehingga Mandor yang punya kegiatan ke-6 berstatus lembur (tanda lembur ada pada RENCANA terkait, field `lembur`) terhitung 0 hari Lembur. Perbaiki: satu tanggal dihitung "hari Lembur" bila SALAH SATU benar: (1) rencana terkait (rencanaId) punya field `lembur`; (2) laporan punya `ritase` > 4; (3) laporan punya `lemburDisetujui`; (4) laporan punya `alasanLembur`; (5) penanda LEMBUR pada tanda laporan. Satu tanggal tetap dihitung SATU kali per orang.
b. HAPUS dari teks perintah ke agen baris catatan pengembang: "Tahap 4b-1 belum memproses jawaban agen; pemrosesan jawaban ada di 4b-2." (di formatJawabanReport). Agen tidak boleh menerima baris itu.
Selain a dan b jangan mengubah bagian 4b-1.

## BUTIR 1 — Tempel dan baca jawaban agen
Kotak tempel jawaban -> tombol "Baca hasil" (pratinjau; wajib baca ulang bila teks berubah setelah Baca, seperti di tab Agen). Pratinjau menampilkan perbandingan angka agen vs angka acuan aplikasi, dengan SELISIH diberi warna. Baris dengan kata kunci lain ditandai merah dan tidak dipakai.

## FORMAT JAWABAN AGEN (parser persis ini; satu baris per item, pemisah " | ")
REKAP | periode | nama | peran | hari kerja | ritase | hari Lembur | hari libur | catatan
MATRIKS | tanggal | kegiatan | orang | rencana | realisasi | catatan
BELUM FINAL | ID laporan | alasan
SELISIH | item | angka agen | angka acuan | catatan
CATATAN KLIEN | paragraf
Lalu satu baris sumber global di akhir. Baris dengan kata kunci lain = ditandai merah di pratinjau, tidak dipakai.

## BUTIR 2 — Persetujuan
Pengawas/Admin memeriksa pratinjau, centang "sudah saya periksa", lalu "Setujui report". Baru setelah itu tombol "Unduh Excel" aktif. Tanpa persetujuan tidak ada unduhan. Audit Log mencatat SATU baris (siapa, periode, jenis, jumlah SELISIH).

## BUTIR 3 — Excel (pakai penulis XLSX yang sudah ada; tambahkan gaya fill/tebal di styles.xml)
- Matriks klien: satu lembar, 31 kolom tanggal; baris Rencana berlatar kuning; tanggal tidak valid (mis. 31 di bulan 30 hari) abu-abu; kolom "Total Aktivitas"; CATATAN KLIEN di bawah.
- Rekap penggajian: 3 lembar ("Rekap per orang", "Rincian per tanggal", "Catatan & selisih"). TANPA kolom gaji/rupiah.

Mulai kerjakan sekarang.
