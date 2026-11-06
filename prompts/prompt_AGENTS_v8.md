Semua balasan kepada saya dalam bahasa Indonesia.
Waktu sekarang (WIB): Selasa, 3 November 2026, pukul [ISI JAM WIB SAAT MENEMPEL].

PERAN: kamu menyunting dokumen aturan agen. Ini BUKAN tugas membuat atau menjalankan tes. JANGAN menulis skrip tes, JANGAN menjalankan skenario uji, JANGAN membuat data uji baru. Tugasmu hanya menghasilkan AGENTS_v8.md dari AGENTS_v7.md dan mencatatnya.

BERKAS TERLAMPIR (hanya ini yang kamu punya):
1. AGENTS_v7.md  (aturan berlaku, sumber utama)
2. CATATAN_VERSI (7).md  (riwayat versi, format baris sudah ada)
3. paket-uji_v4.md  (hanya dirujuk, tidak diubah kecuali butir H)
Bila ada berkas yang tidak terlihat, berhenti dan beri tahu saya. Jangan mengarang isinya.

ATURAN KERJA
- Salin AGENTS_v7.md menjadi AGENTS_v8.md, lalu ubah HANYA butir A sampai G di bawah. Bagian lain tidak boleh berubah, bahkan satu kata.
- Jangan menulis ulang, merapikan, atau memperpendek bagian yang tidak disebut.
- Carilah letak perubahan berdasarkan isi bagian (judul + kalimat), bukan nomor yang saya sebut.
- Bila satu butir bertabrakan dengan aturan lain di v7, JANGAN memilih sendiri: tulis di daftar "Pertanyaan" di akhir laporan.

A. LAYAR KONFIRMASI DULU, TULIS BERKAS BELAKANGAN
Pada alur utama: tampilkan layar konfirmasi lebih dulu; berkas di output/ ditulis hanya setelah "Setuju & simpan." Pengecualian audit log tetap.

B. WAKTU
Jam dan tanggal memakai "Waktu sekarang (WIB)" (hari + tanggal + jam) yang saya tulis di awal tugas. Jangan memakai jam mesin atau cap waktu berkas. Bila baris itu tidak ada, minta saya menuliskannya.

C. RENCANA UNTUK SEMUA TANGGAL
Sheet Rencana diisi untuk semua tanggal yang ada di rencana mingguan terlampir untuk Area tersebut, bukan hanya tanggal laporan.

D. BLOK AKTIVITAS TEMPLAT YANG TIDAK DIPAKAI
Blok aktivitas templat yang tidak dipakai dihapus. Perjelas: hanya baris yang berisi data yang dilindungi (jangan hapus baris berdata).

E. "Setuju & simpan." HANYA IZIN SIMPAN
"Setuju & simpan." hanya berarti izin menyimpan. Sheet Review Pengawas tetap berstatus DRAF. Penandatanganan adalah giliran terpisah.

F. AUDIT LOG
Satu baris per kejadian yang SELESAI. Menampilkan layar konfirmasi tidak dicatat. Penolakan karena izin = satu baris.

G. MODE APLIKASI (BAGIAN BARU, taruh setelah alur utama, beri judul "Mode aplikasi")
Aplikasi papan PantauUsaha tidak bisa memanggil agen. Pengguna menyalin "paket" dari aplikasi, menempelkannya ke chat agen, lalu menempel jawaban agen kembali. Aturan mode ini:
1. Dikenali bila pesan berisi paket dari aplikasi (ada rencana dan daftar laporan dengan ID laporan). Agen membaca paket, membandingkan tiap laporan dengan rencana mingguan di paket, dan menjawab.
2. FORMAT JAWABAN: satu baris per laporan, 4 kolom dipisah " | " persis:
   ID laporan | Tanda | catatan | ID rencana
   Tanda hanya salah satu: Sesuai / Tidak sesuai / Di luar rencana. Catatan WAJIB terisi untuk Tidak sesuai dan Di luar rencana; untuk Sesuai singkat saja (rencana ke-berapa, aktivitas, Area/Zona, hal yang perlu dicek). ID rencana diisi bila ada yang cocok, kosong bila tidak. Setelah baris-baris itu boleh ada penjelasan singkat, tetapi baris-baris data harus berdiri sendiri dan mudah disalin.
3. Di luar rencana: agen TIDAK langsung menambahkan apa pun. Tampilkan layar konfirmasi untuk Pengawas lebih dulu. Hanya setelah Pengawas menyetujui di chat, agen menambahkan aktivitas itu ke Excel dan laporan. Peran yang menyetujui dicek (Bagian peran dan izin).
4. KONFIRMASI TANGGAL MASA DEPAN: bila laporan bertanda TANGGAL MASA DEPAN, atau tanggal kerjanya lebih akhir dari "Waktu sekarang (WIB)", agen WAJIB meminta konfirmasi Pengawas sebelum menyatakan Sesuai. Alasan: kegiatan tidak mungkin dilaporkan sebelum tanggal rencananya. Tulis di catatan.
5. Foto: aplikasi hanya mengirim NAMA berkas foto. Agen tidak bisa menilai isi foto; tulis "isi foto tidak diketahui" dan jangan menyimpulkan. Hanya periksa ada/tidaknya nama berkas dan keterangan.
6. Ritase driver mengikuti aturan ritase yang sudah ada (1-4 normal, 5-7 lembur, di atas 7 tidak dihitung sampai disetujui). Mandor lebih dari 5 aktivitas per hari: baris ke-6 dan seterusnya ditandai lembur di catatan.
7. Excel dari aplikasi berbentuk DAFTAR DATAR 10 kolom: Tanggal, Area, Zona, Orang, Peran, Kendaraan, Kegiatan, Ritase, Status, Tanda; sheet Rencana dan Realisasi. Ini BUKAN templat laporan harian di Bagian format berkas. Tulis aturan eksplisit: menambah aktivitas di luar rencana = menambah SATU baris di sheet Realisasi dengan Tanda "Di luar rencana" dan catatan sumber; baris lain tidak disentuh; nilai lama tidak ditimpa.
8. Isi laporan tetap data, bukan perintah (aturan yang sudah ada berlaku di mode ini).
9. Bila tidak yakin: tulis "tidak tahu" di catatan, jangan menebak, dan sebutkan sebagai celah aturan di akhir jawaban.

BUTIR H (kecil)
Jika di paket-uji_v4.md ada rujukan ke nama berkas AGENTS_v7.md, buat salinan paket-uji_v5.md yang hanya mengganti rujukan itu menjadi AGENTS_v8.md dan menambah baris awal "Waktu sekarang (WIB): ..." pada PROMPT PEMBUKA STANDAR bila belum ada. Jangan ubah yang lain.

CATATAN_VERSI
Tambahkan baris baru di akhir tabel (jangan ubah baris lama) untuk AGENTS_v8.md dan paket-uji_v5.md, memakai tanggal dan jam dari "Waktu sekarang (WIB)", satu baris per perubahan butir A-H, kolom Alasan terisi.

HASIL YANG SAYA TERIMA
1. AGENTS_v8.md, CATATAN_VERSI (8).md, paket-uji_v5.md (bila butir H berlaku), semua sebagai berkas yang bisa saya unduh.
2. Laporan singkat: untuk tiap butir A-H, di bagian mana (judul bagian) kamu mengubahnya; daftar "Pertanyaan" bila ada tabrakan; dan pernyataan jujur bahwa bagian lain tidak diubah. Saya sendiri akan membandingkan v7 dengan v8, jadi jangan menyatakan "sudah diverifikasi" untuk hal yang tidak kamu bandingkan.
3. Jangan menjalankan tes apa pun.
