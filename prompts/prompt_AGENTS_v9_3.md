Semua balasan kepada saya dalam bahasa Indonesia.
Waktu sekarang (WIB): [ISI: hari, tanggal, jam WIB]

# AGENTS v9 — LANGKAH 3 dari 4 (butir N, O, P)

PERAN: kamu menyunting dokumen aturan agen. Ini BUKAN tugas membuat atau menjalankan tes. JANGAN menulis skrip tes, JANGAN menjalankan skenario uji, JANGAN membuat data uji baru.

LANJUTAN di chat yang sama: pakai AGENTS_v9.md yang sudah ada (hasil langkah 2). Ubah HANYA butir N, O, dan P.

ATURAN KERJA
- Ubah HANYA butir yang disebut di bawah. Bagian lain tidak boleh berubah, bahkan satu kata. Jangan menulis ulang, merapikan, atau memperpendek.
- Carilah letak perubahan berdasarkan isi bagian (judul + kalimat), bukan nomor yang saya sebut.
- Bila satu butir bertabrakan dengan aturan lain, JANGAN memilih sendiri: tulis di daftar "Pertanyaan" di akhir laporan.
- Perubahan pada Mode aplikasi dilakukan di bagian "Mode aplikasi" yang sudah ada; ubah butir yang bersangkutan atau tambahkan butir baru bernomor lanjutan.
- Kerjakan langsung dengan edit terarah; jangan membaca ulang seluruh berkas berkali-kali.
- Di akhir tulis laporan singkat: tiap butir diubah di bagian (judul) mana, daftar "Pertanyaan", dan pernyataan jujur bahwa bagian lain tidak diubah. Jangan menyatakan "sudah diverifikasi" untuk hal yang tidak kamu bandingkan.

N. AGEN TIDAK MENULIS APA PUN TANPA PERSETUJUAN (PENGECUALIAN AUDIT LOG DIHAPUS)
Keputusan Rany: pengecualian "audit log ditulis langsung oleh agen" dihapus. Ubah semua tempat yang menyebutnya (cari kata "langsung" dan "pengecualian": Bagian 0 baris output/audit-log, Bagian 9.2, Bagian 9.3, Bagian 9.8, dan butir lain yang menyebutnya). Aturan baru:
1. Baris audit log yang diusulkan ditampilkan di layar konfirmasi bersama hasil kerja dan ditulis HANYA setelah "Setuju & simpan".
2. Untuk kejadian yang tidak menulis berkas (penolakan, menunggu, klarifikasi), agen menampilkan blok "Catatan audit yang diusulkan" dan bertanya apakah dicatat. Ditulis hanya bila pengguna menyetujui.
3. Di Mode aplikasi agen tidak menulis audit log sama sekali; aplikasi yang mencatat.
4. Di Bagian 0, kolom akses output/audit-log menjadi "Tulis, hanya lewat konfirmasi". Bagian 9.3 "Tanpa aksi langsung" berlaku tanpa pengecualian.
Bila perubahan ini bertabrakan dengan contoh atau kasus uji di v8, JANGAN mengubah contoh/kasus uji sendiri; tulis di "Pertanyaan".

O. KEGIATAN BELUM DILAPORKAN (agen membantu Pengawas)
Tambahkan butir Mode aplikasi baru. Keputusan Rany: agen memberi tahu Pengawas bila ada kegiatan Mandor atau Area yang belum dikerjakan atau belum dilaporkan.
1. Paket review akan memuat blok "RENCANA HARI INI" (semua baris rencana tanggal itu, termasuk yang belum ada laporannya). Bila blok tidak ada, agen menulis "tidak tahu" untuk pemeriksaan ini dan menyebutnya sebagai celah.
2. Untuk tiap baris rencana yang tidak punya laporan, agen menjawab satu baris format 4 kolom: ID laporan diisi "-", Tanda `Belum dilaporkan`, catatan = nama Mandor/Driver, Kegiatan, Area/Zona, tanggal, ID rencana di kolom 4.
3. Sampai tanggal kerja + 1 hari pukul 23.59 WIB, Tanda tetap `Belum dilaporkan`. Lewat dari itu Tanda tetap sama, tetapi catatan diawali `[Lewat batas]` agar Pengawas tahu sudah melewati batas laporan (butir J).
4. Setelah baris-baris data, agen menulis satu ringkasan pendek DIKELOMPOKKAN per Mandor dan per Area: siapa dan wilayah mana yang belum mengerjakan atau melaporkan kegiatan. Agen tidak menyimpulkan bahwa pekerjaan tidak dikerjakan; ia hanya menyatakan belum ada laporan.
5. Agen tidak menghubungi siapa pun (Bagian 9.3); Pengawas yang menindaklanjuti.

P. REPORT MINGGUAN DAN BULANAN (Mode aplikasi)
Tambahkan butir Mode aplikasi baru untuk dua jenis report. Keputusan Rany: aplikasi menghitung angka acuan; agen menghitung sendiri dari data mentah, mencocokkan, dan menandai selisih; Admin atau Pengawas memverifikasi dan menyetujui; agen tidak menghitung gaji, upah, lembur, insentif, atau potongan (Bagian 8.4 tetap berlaku).
1. Paket "report" memuat: jenis report, periode, data laporan CLOSED pada periode itu, laporan yang belum final, dan ANGKA ACUAN dari aplikasi. Bila salah satu tidak ada, agen menyebutnya sebagai celah dan tidak mengarang angka.
2. Aturan hitung mengikuti Bagian 8 (rekap penggajian: periode Sabtu-Jumat, hanya laporan Disetujui/CLOSED, susulan, hari libur, hari Lembur) dan Bagian 10 (matriks Rencana vs Realisasi bulanan untuk klien).
3. Format jawaban (tetap; dibagi dengan build 4, jangan diubah): setiap baris diawali kata kunci dan dipisah tanda "|":
   - REKAP | periode | nama | peran | hari kerja | ritase | hari Lembur | hari libur | catatan
   - MATRIKS | tanggal | kegiatan | orang | rencana | realisasi | catatan
   - BELUM FINAL | ID laporan | alasan
   - SELISIH | item | angka agen | angka acuan | catatan
   - CATATAN KLIEN | satu paragraf ringkas untuk klien (bila jenis report = laporan klien)
   Setelah baris data, satu baris sumber global.
4. Bila angka agen berbeda dari angka acuan, agen TIDAK memilih salah satu; ia menulis baris SELISIH dan menyerahkan keputusan kepada Admin atau Pengawas.
5. Agen tidak menulis berkas dan tidak menyetujui report. Pembuatan Excel dan pencatatan persetujuan dijalankan aplikasi.

Selesai langkah ini: simpan AGENTS_v9.md dan berhenti.
