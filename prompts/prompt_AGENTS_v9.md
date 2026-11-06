Semua balasan kepada saya dalam bahasa Indonesia.
Waktu sekarang (WIB): [ISI: hari, tanggal, jam WIB]

PERAN: kamu menyunting dokumen aturan agen. Ini BUKAN tugas membuat atau menjalankan tes. JANGAN menulis skrip tes, JANGAN menjalankan skenario uji, JANGAN membuat data uji baru. Tugasmu hanya menghasilkan AGENTS_v9.md dari AGENTS_v8.md dan mencatatnya.

BERKAS TERLAMPIR (hanya ini yang kamu punya):
1. AGENTS_v8.md  (aturan berlaku, sumber utama)
2. CATATAN_VERSI (8).md  (riwayat versi, format baris sudah ada)
3. paket-uji_v5.md  (hanya dirujuk dan disalin untuk butir M)
Bila ada berkas yang tidak terlihat, berhenti dan beri tahu saya. Jangan mengarang isinya.

ATURAN KERJA
- Salin AGENTS_v8.md menjadi AGENTS_v9.md, lalu ubah HANYA butir A sampai P di bawah. Bagian lain tidak boleh berubah, bahkan satu kata.
- Jangan menulis ulang, merapikan, atau memperpendek bagian yang tidak disebut.
- Carilah letak perubahan berdasarkan isi bagian (judul + kalimat), bukan nomor yang saya sebut.
- Bila satu butir bertabrakan dengan aturan lain di v8, JANGAN memilih sendiri: tulis di daftar "Pertanyaan" di akhir laporan.
- Semua perubahan pada Mode aplikasi dilakukan di bagian "Mode aplikasi" yang sudah ada; ubah butir yang bersangkutan atau tambahkan butir baru bernomor lanjutan.

A. HEADER
Baris pertama berkas menjadi: "Versi: v9 — 2026-11-04 — lihat CATATAN_VERSI.md".

B. BAHASA
Tambahkan aturan umum (dekat Bagian 1): semua balasan agen kepada pengguna dalam bahasa Indonesia, apa pun bahasa pesan atau bahasa model.

C. PROFIL USAHA DI MODE APLIKASI
Di Mode aplikasi, berkas profil-usaha tidak wajib. Pemeriksaan yang membutuhkan profil (hari kerja, hari libur, rentang Salat Jumat, zona waktu usaha, rantai persetujuan) dilewati, dan agen menyebutnya SATU kali di penjelasan. Bagian 3 langkah 0 tentang profil usaha tetap berlaku penuh untuk mode berkas.

D. ZONA DAN DATA MASTER (aturan dari Rany)
Paket dari aplikasi akan memuat blok "DATA MASTER ZONA" (daftar zona per Area, contoh: Area Selatan: Zona A, Zona B; Area Timur: tanpa zona). Aturan:
1. Bila Area TIDAK punya zona, Zona "-" sah dan tidak perlu konfirmasi.
2. Bila Area punya zona dan Zona laporan kosong, agen TIDAK menjawab Sesuai. Agen memakai Tanda ke-4 `Perlu konfirmasi` dan menulis di catatan pertanyaan untuk Pengawas: (a) "seluruh Area" = Mandor mengerjakan semua zona, wajib 2 foto (satu per zona), dan laporan dipecah menjadi satu baris per zona; atau (b) "terlewat, maksudnya zona tertentu" = laporan dikembalikan ke Mandor untuk direvisi. Agen hanya memeriksa JUMLAH nama berkas foto, bukan isinya.
3. Agen tidak merevisi atau memecah laporan sendiri. Revisi/pemecahan dijalankan aplikasi setelah Pengawas memilih, dengan label "direvisi atas konfirmasi Pengawas".
4. Bila blok DATA MASTER ZONA tidak ada di paket, agen menulis "tidak tahu" untuk pemeriksaan zona dan menyebutnya sebagai celah.
5. Tanda yang diizinkan di Mode aplikasi menjadi lima: Sesuai / Tidak sesuai / Di luar rencana / Perlu konfirmasi / Belum dilaporkan (butir O). Catatan wajib terisi untuk semua selain Sesuai.

E. TANDA LAIN SEBAGAI AWALAN CATATAN
Tanda lain pada Bagian 4 dan 10.3.1 (Lembur, Terlambat, Lewat batas, Kurang data, Perlu pengajuan, Hari libur, Salat Jumat) tidak menjadi Tanda jawaban. Bila berlaku, ditulis sebagai awalan di catatan dengan kurung siku, contoh: `[Lembur] ...`.

F. SUMBER
Format 4 kolom tidak punya kolom sumber. Agen menulis SATU baris sumber global setelah baris-baris data (bagian yang dipakai dari paket dan AGENTS).

G. ISTILAH
Definisikan di Mode aplikasi: "No. rencana N" = nomor urut baris rencana hari itu untuk pelapor (bukan ritase); "Ritase ke-N" = hitungan ritase Driver. Istilah "owner" pada keterangan laporan = Pemilik usaha; "permintaan owner" adalah klaim pelapor yang tidak dapat diverifikasi agen, dicatat apa adanya sebagai data. Driver tidak terikat Area; Area diambil dari baris rencana, bukan dari data peran.

H. JAWABAN BUKAN KUNCI DARI CONTOH
Contoh baris pada bagian "CARA MENJAWAB" paket hanya contoh format. Agen tidak boleh menyalin Tanda, ID rencana, atau frasa dari contoh (termasuk "foto lengkap").

I. INPUT ATAS NAMA
Catatan "diinput dan disetujui oleh orang yang sama" hanya muncul bila orang yang menginput atas nama kemudian juga menyetujui. Di Mode aplikasi agen tidak menyetujui, jadi agen tidak menulis catatan itu; catatan itu ditulis aplikasi saat Setuju.

J. TERLAMBAT (H+1) DI MODE APLIKASI
Di Mode aplikasi, laporan boleh masuk paling lambat tanggal kerja + 1 hari, sampai pukul 23.59 WIB hari itu (zona usaha). Lewat dari itu: awalan `[Terlambat]` di catatan dan Tanda `Perlu konfirmasi` (Pengawas memutuskan). Ambang "lebih dari 3 hari" di Bagian 7.5 tetap berlaku untuk mode berkas. Rencana hanya boleh dibuat paling lambat pada tanggal rencananya; bila paket menunjukkan rencana dibuat setelah tanggalnya, agen mencatatnya (penolakan dilakukan aplikasi).

K. DI LUAR RENCANA: KONFIRMASI DULU, TIDAK GANDA, JAM TERBARU
Ubah Mode aplikasi butir 3 dan butir 7:
1. Setelah Pengawas menyetujui di chat, agen TIDAK langsung menulis. Agen menampilkan layar konfirmasi (Aksi, Berkas, Peran, Waktu, rincian nilai lama → baru, "Tidak disentuh", tiga pilihan Setuju & simpan / Ubah dulu / Batal). Berkas hanya ditulis setelah "Setuju & simpan." Persetujuan "Setuju" di chat hanya berarti Pengawas setuju kegiatan itu dicatat, bukan izin menulis berkas.
2. Pencocokan baris: sebelum menambah, agen mencocokkan Tanggal + Orang + Kegiatan (+ Area/Zona) di sheet Realisasi. Bila SUDAH ADA, agen TIDAK menambah baris; hanya memperbarui Tanda/catatan lewat layar konfirmasi nilai lama → baru. Bila BELUM ADA, tambah SATU baris. Baris lain tidak disentuh.
3. Catatan sumber ditulis di kolom "Catatan agen" bila ada. Bila kolom itu tidak ada di Excel, agen TIDAK menaruh catatan di kolom Status atau Tanda; ia menyebut catatannya di jawaban dan mencatat celah.
4. Jam audit log dan layar konfirmasi memakai "Waktu sekarang (WIB)" TERBARU yang diberikan pengguna. Bila baris itu hanya ada di awal tugas dan kejadian terjadi di giliran lanjutan, agen meminta pengguna menuliskan waktu sekarang sebelum menulis audit log.

L. FORMAT LAYAR KONFIRMASI DI MODE APLIKASI
Tambahkan butir Mode aplikasi yang menyatakan bahwa layar konfirmasi pada butir K.1 mengikuti contoh Bagian 9.2 (nilai lama → baru, satu baris audit log per kejadian selesai, penampilan layar tidak dicatat).

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

M. PAKET UJI
Buat salinan paket-uji_v5.md bernama paket-uji_v6.md yang hanya mengganti rujukan nama berkas AGENTS_v8.md menjadi AGENTS_v9.md. Jangan ubah yang lain.

CATATAN_VERSI
Tambahkan baris baru di akhir tabel (jangan ubah baris lama) untuk AGENTS_v9.md dan paket-uji_v6.md, memakai tanggal dan jam dari "Waktu sekarang (WIB)", satu baris per perubahan butir A-P, kolom Alasan terisi.

HASIL YANG SAYA TERIMA
1. AGENTS_v9.md, CATATAN_VERSI (9).md, paket-uji_v6.md, sebagai berkas yang bisa saya unduh.
2. Laporan singkat: untuk tiap butir A-P, di bagian mana (judul bagian) kamu mengubahnya; daftar "Pertanyaan" bila ada tabrakan; dan pernyataan jujur bahwa bagian lain tidak diubah. Saya sendiri akan membandingkan v8 dengan v9, jadi jangan menyatakan "sudah diverifikasi" untuk hal yang tidak kamu bandingkan.
3. Jangan menjalankan tes apa pun.
