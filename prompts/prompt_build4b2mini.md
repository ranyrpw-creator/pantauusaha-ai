Semua balasan kepada saya dalam bahasa Indonesia.
Waktu sekarang (WIB): [ISI: hari, tanggal, jam WIB]

# BUILD 4b-2 MINI — Perbaikan kecil menu Report (v5a -> v5)

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

## BUTIR 1 — Perbaikan dari pemeriksaan v5a (HANYA ini; dua perubahan kecil)
a. HITUNG HARI LEMBUR MANDOR (kekeliruan): fungsi adaLemburReport / hitungAngkaAcuan sekarang hanya melihat data laporan, sehingga Mandor yang punya kegiatan ke-6 berstatus lembur (tanda lembur ada pada RENCANA terkait, field `lembur`) terhitung 0 hari Lembur. Perbaiki: satu tanggal dihitung "hari Lembur" bila SALAH SATU benar: (1) rencana terkait (rencanaId) punya field `lembur`; (2) laporan punya `ritase` > 4; (3) laporan punya `lemburDisetujui`; (4) laporan punya `alasanLembur`; (5) penanda LEMBUR pada tanda laporan. Satu tanggal tetap dihitung SATU kali per orang.
b. HAPUS dari teks perintah ke agen baris catatan pengembang: "Tahap 4b-1 belum memproses jawaban agen; pemrosesan jawaban ada di 4b-2." (di formatJawabanReport). Agen tidak boleh menerima baris itu.
Jangan membuat fitur lain (pembaca jawaban, persetujuan, Excel TIDAK dikerjakan sekarang). Cari fungsi dengan nama (adaLemburReport, hitungAngkaAcuan, formatJawabanReport), edit langsung, jangan membaca seluruh berkas.


Mulai kerjakan sekarang.
