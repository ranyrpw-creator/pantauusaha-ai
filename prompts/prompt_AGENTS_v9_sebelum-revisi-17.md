Semua balasan kepada saya dalam bahasa Indonesia.
Waktu sekarang (WIB): Rabu, 4 November 2026, pukul [ISI JAM WIB SAAT MENEMPEL].

PERAN: kamu menyunting dokumen aturan agen. Ini BUKAN tugas membuat atau menjalankan tes. JANGAN menulis skrip tes, JANGAN menjalankan skenario uji, JANGAN membuat data uji baru. Tugasmu hanya menghasilkan AGENTS_v9.md dari AGENTS_v8.md dan mencatatnya.

BERKAS TERLAMPIR (hanya ini yang kamu punya):
1. AGENTS_v8.md  (aturan berlaku, sumber utama)
2. CATATAN_VERSI (8).md  (riwayat versi, format baris sudah ada)
3. paket-uji_v5.md  (hanya dirujuk dan disalin untuk butir M)
Bila ada berkas yang tidak terlihat, berhenti dan beri tahu saya. Jangan mengarang isinya.

ATURAN KERJA
- Salin AGENTS_v8.md menjadi AGENTS_v9.md, lalu ubah HANYA butir A sampai N di bawah. Bagian lain tidak boleh berubah, bahkan satu kata.
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
5. Tanda yang diizinkan di Mode aplikasi menjadi empat: Sesuai / Tidak sesuai / Di luar rencana / Perlu konfirmasi. Catatan wajib terisi untuk semua selain Sesuai.

E. TANDA LAIN SEBAGAI AWALAN CATATAN
Tanda lain pada Bagian 4 dan 10.3.1 (Lembur, Terlambat, Kurang data, Perlu pengajuan, Hari libur, Salat Jumat) tidak menjadi Tanda jawaban. Bila berlaku, ditulis sebagai awalan di catatan dengan kurung siku, contoh: `[Lembur] ...`.

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

N. TERUSKAN CATATAN PENGAWAS KE PELAPOR (laporan DIKEMBALIKAN KE AGEN)
Tambahkan butir Mode aplikasi baru. Paket "teruskan catatan Pengawas ke <peran>" meminta agen menulis teks yang siap diteruskan ke Mandor atau Driver. Aturan:
1. Agen hanya MENULIS DRAF pesan. Agen tidak mengirim apa pun kepada siapa pun (Bagian 9.3); Pengawas yang meneruskan.
2. Pesan memuat alasan Pengawas APA ADANYA (tidak diubah, dikurangi, atau ditambah), identitas laporan (tanggal, kegiatan, Area/Zona), dan apa yang perlu diperbaiki sesuai alasan itu. Nada sopan, singkat, bahasa Indonesia.
3. Bila alasan Pengawas kosong atau tidak jelas, agen meminta penjelasan dan tidak mengarang alasan.
4. Agen tidak mengubah data atau status laporan, dan tidak menilai isi foto.
5. Bila pengembalian terjadi karena konfirmasi zona (butir D), pesan menyebut pilihan Pengawas (zona tertentu) dan meminta Mandor memperbaiki laporan.
6. Format jawaban: satu blok "PESAN UNTUK <nama>:" diikuti teks pesan, lalu satu baris sumber global. Bukan baris 4 kolom.
7. ID laporan TETAP. Pelapor memperbaiki laporan yang sama di aplikasi; perubahan status (DIKEMBALIKAN KE AGEN -> MENUNGGU AGEN) dan pencatatan riwayat dijalankan aplikasi, bukan agen.
8. Catatan Pengawas saat mengembalikan laporan adalah ALASAN PENGEMBALIAN (riwayat laporan dan sheet "Review Pengawas"), bukan Temuan atau Kendala. Temuan/Kendala hanya dicatat lewat alurnya sendiri (Bagian 5) atas permintaan yang berwenang.
9. Menyusun draf pesan bukan kejadian yang menulis berkas, jadi tidak membuat baris audit log oleh agen. Pengembalian dan penerusan dicatat aplikasi. Paket jenis ini tidak memuat rencana mingguan dan dikenali dari kalimat "teruskan catatan Pengawas"; format 4 kolom TIDAK dipakai.

M. PAKET UJI
Buat salinan paket-uji_v5.md bernama paket-uji_v6.md yang hanya mengganti rujukan nama berkas AGENTS_v8.md menjadi AGENTS_v9.md. Jangan ubah yang lain.

CATATAN_VERSI
Tambahkan baris baru di akhir tabel (jangan ubah baris lama) untuk AGENTS_v9.md dan paket-uji_v6.md, memakai tanggal dan jam dari "Waktu sekarang (WIB)", satu baris per perubahan butir A-N, kolom Alasan terisi.

HASIL YANG SAYA TERIMA
1. AGENTS_v9.md, CATATAN_VERSI (9).md, paket-uji_v6.md, sebagai berkas yang bisa saya unduh.
2. Laporan singkat: untuk tiap butir A-N, di bagian mana (judul bagian) kamu mengubahnya; daftar "Pertanyaan" bila ada tabrakan; dan pernyataan jujur bahwa bagian lain tidak diubah. Saya sendiri akan membandingkan v8 dengan v9, jadi jangan menyatakan "sudah diverifikasi" untuk hal yang tidak kamu bandingkan.
3. Jangan menjalankan tes apa pun.
