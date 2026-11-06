# Catatan perubahan tertunda (backlog) — belum dikerjakan, Rany masih mencoba aplikasi

Format: tanggal/jam WIB — sumber — isi — status

## 3 Nov 2026, 18.36 — masukan Rany saat mencoba menu Rencana Mingguan (app v2, md5 b49335eb…)
1. SPV harus bisa MEREVISI rencana yang sudah disimpan (contoh: Area ternyata punya Titik; saat ini hanya ada tombol Hapus). -> perubahan aplikasi.
2. Bila SPV tidak memilih Titik, agen perlu KONFIRMASI ke SPV: tugas itu untuk seluruh titik di lokasi tersebut, atau salah satu titik. Ini TUGAS TAMBAHAN agen (tugas B: pemeriksaan rencana; tugas A tetap pembandingan laporan).
3. Setelah SPV menyimpan rencana, agen memeriksa data dan HANYA meminta konfirmasi bila kolom Titik tidak diisi. Setelah SPV mengonfirmasi, baru agen yang mengedit.

Status: dicatat saja. Belum ada keputusan membangun.

## Pertanyaan terbuka (tanyakan saat Rany siap)
- Konfirmasi hanya bila Area itu punya >=1 Titik di Master Data? (Area tanpa Titik tidak perlu ditanya.)
- Bila jawabannya "seluruh titik": satu baris berlabel "Seluruh titik", atau dipecah satu baris per titik (mempengaruhi kuota 5 kegiatan/orang/hari)?
- Bentuk jawaban agen untuk tugas B (mis. `ID rencana | Seluruh titik` atau `ID rencana | Titik A`) dan siapa yang menempel balik ke aplikasi.
- Prioritas terhadap batas keputusan Rabu 4 Nov 12.00 WIB (tugas B menambah: paket perintah di layar Rencana, bagian AGENTS_v8, uji).

## 3 Nov 2026, 18.45 — jawaban Rany atas pertanyaan terbuka (masih dicatat, belum dibangun)
Aturan Zona (menggantikan "Titik"):
- "Titik" diganti "Zona". Zona diinput di Master Data per Area. Dasar bisnis: usaha jasa sudah menghitung berapa meter wilayah yang bisa dikerjakan 1 petugas; area luas dibagi beberapa zona.
- Area punya zona (mis. A dan B) dan SPV tidak memilih zona -> agen WAJIB konfirmasi ke SPV (artinya tugas untuk seluruh zona = 2 foto evidence; bila satu zona dipilih = cukup 1 foto).
- Jawaban "seluruh zona" -> rencana DIPECAH satu baris per zona.
- Area tanpa zona di Master Data -> tidak perlu bertanya (rencana untuk seluruh area, 1 foto). Prinsip umum brief: bila agen bingung, agen memastikan dan meminta konfirmasi.
- Agen memeriksa rencana terhadap Master Data (area punya zona atau tidak) setelah SPV menyimpan rencana.
Kuota:
- Maksimal 5 aktivitas per orang per hari DIKUNCI sebagai aturan. Bila ternyata lebih (termasuk akibat pemecahan per zona) -> agen minta konfirmasi SPV dan kelebihannya DIHITUNG LEMBUR. (Mengubah keputusan lama: sebelumnya baris ke-6 ditolak.)
Jawaban agen yang kembali ke aplikasi:
- Revisi dan perbaikan rencana sesuai konfirmasi Pengawas, dengan penjelasan rinci ("bahwa ...").
Revisi manual SPV: lihat catatan 18.36 butir 1 (tombol Edit rencana).

## Perubahan yang akan jadi satu paket build berikutnya (usulan Claude, tunggu trial selesai)
Aplikasi: Titik->Zona; Master Data Zona per Area; Edit rencana; kuota >5 = konfirmasi + LEMBUR (bukan ditolak); tombol "Salin perintah cek rencana"; terima revisi agen; label "direvisi atas konfirmasi Pengawas" + cap waktu; Excel memuat Zona.
AGENTS_v8: tugas A (bandingkan laporan) + tugas B (cek rencana: zona, kuota, ragu -> konfirmasi), layar konfirmasi, format jawaban revisi.
Pertanyaan yang masih terbuka: (a) lembur >5 berlaku juga untuk Mandor dan siapa yang menandai; (b) siapa mengelola Zona (default Admin); (c) bentuk baku jawaban revisi agar bisa diterapkan aplikasi.

## 3 Nov 2026, 19.11 — keputusan Rany atas tiga pertanyaan terbuka
- Lembur >5 aktivitas berlaku juga untuk Mandor; ditandai agen; disetujui SPV di konfirmasi yang sama. -> YA
- ZONA DIKELOLA PENGAWAS (bukan Admin). Master Data dikelola bersama Admin dan Pengawas. Titik kritis: SETIAP perubahan Master Data harus terekam (audit). Bila ada perubahan yang sebenarnya berubah (contoh: Area Selatan 2 zona -> 3 zona), agen mengonfirmasi ke Admin DAN Pengawas; keduanya harus sama-sama konfirmasi "iya".
- Jawaban agen = teks penjelasan + baris terstruktur yang bisa diterapkan aplikasi (ID rencana, zona, ada/tidak lembur). -> YA
Dampak: tugas agen C (perubahan Master Data, konfirmasi ganda). Mengubah matriks hak akses lama (FSD AKB: SPV hanya aktivitas) -> harus diungkap sebagai perubahan rancangan di mini-app.
Pertanyaan terbuka: cakupan hak Pengawas di Master Data (semua jenis data atau hanya Zona + Aktivitas); perubahan berlaku langsung atau setelah dua konfirmasi.

## 3 Nov 2026, 19.13 — masalah: data yang diinput hilang di pratinjau WorkBuddy
Dugaan penyebab: pratinjau/peramban bawaan WorkBuddy tidak menyimpan localStorage secara tetap (tiap buka bisa kosong). Uji Chromium (uji2.js, muat ulang) membuktikan logika simpan aplikasi benar; masalahnya lingkungan.
Usulan perbaikan build berikutnya: tombol "Cadangkan data (.json)" dan "Pulihkan data" + (opsional) "Muat data contoh". Peringatan di aplikasi: data hanya di peramban ini.
Prosedur demo: buka berkas .html di Chrome biasa (klik ganda), peramban dan profil yang sama, bukan Incognito, jangan tekan "Atur ulang data".

## 3 Nov 2026, 20.18 — temuan Rany: terlalu banyak salin satu per satu (tab Agen / Tinjauan)
Diperiksa di kode v2: tombol "Salin perintah untuk agen" per LAPORAN (teksPerintah(lapId)); teks tempel hasil agen disimpan mentah tapi TIDAK di-parse; Tanda dan catatan dipilih manual per laporan. N laporan = N salinan + N pemilihan manual + N tugas WorkBuddy (kredit).
Usulan build berikutnya: (1) "Salin semua yang menunggu" (filter tanggal/Area) -> satu paket berisi banyak laporan + rencana + data peran; (2) agen menjawab satu baris per laporan `ID | Tanda | catatan`; (3) "Tempel hasil" mem-parse dan mengisi Tanda/catatan otomatis, tampil pratinjau, Pengawas menekan Simpan (tetap semua-atau-tidak); baris yang gagal di-parse ditandai. Satu tugas WorkBuddy untuk satu hari.

## 3 Nov 2026, 20.37 — hasil langkah 14 (paket perintah Slamet, laporan idmw0p6geyqy1hu), ulasan Claude
Paket sudah lengkap dan mandiri (kepala AGENTS_v8, identitas, Waktu sekarang WIB, tugas, data laporan, rencana hari itu, data peran, catatan, format jawaban). Temuan untuk build berikutnya:
1. Laporan bertanggal 2026-11-04 dengan keterangan "selesai jam 10.00" dibuat 3 Nov 20.02 (tanggal masa depan). Aplikasi menerimanya. Usulan: peringatan/penolakan laporan bertanggal setelah hari ini. Uji agen yang baik: agen harus menandai kejanggalan ini (Waktu sekarang vs tanggal laporan).
2. Definisi Tanda "Sesuai" menyebut "volume" padahal tidak ada field volume. Hapus "volume" atau jelaskan.
3. Judul bagian "CATATAN PENGAWAS SEBELUMNYA" berisi riwayat sistem ("diinput"), bukan catatan Pengawas. Ganti "RIWAYAT LAPORAN" atau saring hanya catatan Pengawas.
4. Foto hanya nama berkas: tambahkan kalimat "Agen tidak dapat menilai isi foto; hanya memeriksa ada/tidaknya nama berkas."
5. Format jawaban perlu memuat ID rencana yang dicocokkan: `ID laporan | Tanda | catatan | ID rencana` (untuk penerapan otomatis dan Excel).
6. Rencana memuat kegiatan sama di Titik A dan B (Penyapuan x2): ambiguitas pencocokan; akan diselesaikan Zona.
Kunci jawaban yang diharapkan: idmw0p6geyqy1hu | Sesuai | cocok dengan rencana ke-1 (id idmw0ogoysqj6c4: Penyapuan, Area Selatan/Titik A); foto 01_penyapuan.jpg ada; keterangan terisi. CATATAN: tanggal laporan 04/11 dan jam 10.00 lebih awal dari Waktu sekarang (3 Nov 20.36) -> harus disebut sebagai kejanggalan.

## 3 Nov 2026, 20.40 — hasil skenario uji Rany (langkah 1-14; 15-26 belum)
Langkah 1-12 dan 14 LULUS; langkah 13 GAGAL (status laporan di luar rencana hanya "BARU").
Catatan bebas Rany:
1. (Tinggi) Pengawas harus bisa EDIT Master Data (2 PIC sebagai mitigasi bila satu berhalangan). -> keputusan: Master Data dikelola bersama Admin DAN Pengawas (semua jenis data), semua perubahan di Audit Log. Menjawab pilihan (a).
2. (Sedang) Driver tidak terikat area tetapi dibatasi: maks ritase 7 (4 normal + 3 lembur); boleh ditugaskan beberapa area sekaligus tapi total tetap <=7. Pengaturan area Driver belum spesifik.
3. (Sedang) Input >5 aktivitas: baris terakhir di-highlight; seharusnya notifikasi agar Pengawas meninjau dan memilih aktivitas PRIORITAS (bukan otomatis yang terakhir dihapus).
4. (Tinggi) Laporan di luar rencana: status "BARU - DI LUAR RENCANA".
5. (Tinggi) Laporan di luar rencana: wajib kolom Area dan Zona.
Keputusan Rany: lanjutkan build dulu, skenario F dst diuji setelah build.

## 3 Nov 2026, 20.47 — Rany mengonfirmasi 3 asumsi build tahap 3
1. Driver: batas hanya pada RITASE (satu baris rencana = 1 ritase, maks 7), tidak terikat jenis aktivitas; batas 5 kegiatan hanya untuk Mandor. -> YA
2. Mandor >5 aktivitas: Pengawas memilih kurangi atau lanjut dengan kotak centang lembur; nanti agen (tugas B) yang menandai dan meminta. -> YA
3. Laporan bertanggal masa depan: boleh tersimpan dengan tanda TANGGAL MASA DEPAN. Aturan riil: tidak bisa melapor sebelum tanggal rencana; bila terjadi, AGEN WAJIB KONFIRMASI ke Pengawas. -> masuk AGENTS_v8 (tugas A).
Prompt build tahap 3 tidak berubah; sudah dikirim ke Rany 20.40-an.

- 2026-11-03 malam: prompt AGENTS_v8 disusun (prompts/prompt_AGENTS_v8.md): 6 keputusan lama + Mode aplikasi (tugas A) + konfirmasi tanggal masa depan + aturan baris Excel datar. Tugas B dan C menyusul di v9.

- 2026-11-04 07:50: AGENTS_v8 diterima dan dibandingkan dengan v7 (diff): hanya penambahan butir A-G (+62 baris), tidak ada baris v7 yang berubah. Temuan: header berkas masih "Versi: v7 — 2026-11-02" (perbaiki di v9); Mode aplikasi butir 3 belum menyebut lokasi berkas Excel yang ditulis; "Tanda" jawaban agen (3 nilai) berbeda dari "Tanda" di berkas (Terlambat, Hari libur, dst). Saldo kredit 575 (tidak bisa dipakai menghitung biaya, naik dari 566).
- Panduan Peserta Bagian 6: dataset resmi + ~20 test case per tantangan dibagikan saat kickoff; hasil uji + screenshot (termasuk yang gagal) WAJIB; mock data sendiri hanya tambahan. Rany menanyakan ke panitia 4 Nov pagi.

- 2026-11-04 10:30 Hasil uji agen v8 (WorkBuddy, Hy4 preview):
  U1 Sesuai (Slamet Penyapuan): LULUS, 7 kredit; jawaban awal berbahasa Mandarin = GAGAL bahasa (perbaikan: aturan balas Indonesia di AGENTS_v9 + baris pertama paket aplikasi build 4).
  U2 Di luar rencana (Slamet Anti Hama): jawaban LULUS (5 kredit). Giliran persetujuan: agen menulis Excel + audit log tanpa layar konfirmasi nilai lama->baru lebih dulu; menambah baris GANDA Anti Hama (baris sudah ada dari aplikasi) tetapi menandainya jujur; catatan sumber ditaruh di kolom Status; jam audit log 09.07 (jam awal tugas) padahal persetujuan terjadi belakangan.
  Keputusan v9 (usulan): (1) cocokkan Tanggal+Orang+Kegiatan(+Area/Zona), bila ada -> jangan tambah baris, perbarui Tanda/catatan lewat layar konfirmasi lama->baru; (2) Mode aplikasi wajib layar konfirmasi + "Setuju & simpan." sebelum menulis; (3) jam tiap giliran: pakai Waktu sekarang terbaru, bila tidak ada minta; (4) kolom Catatan agen (ke-11) di Excel aplikasi (build 4); (5) header versi; (6) istilah owner = Pemilik; (7) 3 Tanda vs Kurang data; (8) Bagian 7 di Mode aplikasi.

- 2026-11-04 10:40 Catatan Rany untuk build 4 (UX Mandor): (1) tab "Rencana Saya" belum menampilkan progres per baris rencana -> tambah kolom Status (Belum dilapor / Menunggu agen / Menunggu tinjauan / Dikembalikan / Closed) + tombol Lapor yang mengisi formulir otomatis; (2) dropdown Lapor: baris "(sudah dilapor)" masih bisa dipilih -> nonaktifkan kecuali Dikembalikan, atau peringatan + konfirmasi; mencegah laporan ganda.
- Daftar build 4 sejauh ini: kolom Status di Rencana Saya + tombol Lapor; dropdown Lapor menonaktifkan yang sudah dilapor; baris bahasa Indonesia otomatis di paket agen; kolom ke-11 "Catatan agen" di Excel; pintasan Unduh Excel di menu Agen; satu jalur persetujuan (aplikasi) untuk Di luar rencana; label "ke-N dari 4" untuk ritase 5-7; hapus kalimat "(ID rencana dikosongkan di jawaban)" dari label status paket agar tidak terbaca sebagai perintah.

- 2026-11-04 10:42 Konfirmasi Rany (build 4): di menu Lapor, item rencana yang sudah dilaporkan TIDAK BISA diklik (nonaktif) di dropdown. Contoh layar: Slamet sudah lapor 3 aktivitas (Penyapuan, Penyiangan, Anti Hama di luar rencana); ke-1 dan ke-2 berlabel "(sudah dilapor)" tetapi masih bisa dipilih. Perlu diputuskan: pengecualian status Dikembalikan (boleh lapor ulang, usulan saya) dan tetap bisa memilih "Di luar rencana" untuk kegiatan lain; batas 5 per hari Mandor tetap berlaku.

- 2026-11-04 11:25 Keputusan Rany (aturan Zona, pengganti usulan (b)): agen memeriksa Master Data apakah Area punya zona. Bila Area punya zona dan zona kosong -> agen konfirmasi ke Pengawas: (1) seluruh area = Mandor kerjakan semua zona, wajib 2 foto (zona A dan B), laporan dipecah 2 baris; atau (2) Pengawas bilang terlewat dan maksudnya zona tertentu -> agen merevisi setelah konfirmasi Pengawas, status laporan DIKEMBALIKAN KE AGEN dan Mandor diberi tahu. Implikasi: paket agen harus memuat data master zona per Area (build 4); jawaban agen butuh Tanda keempat "Perlu konfirmasi" dengan pertanyaan di catatan; pemecahan 2 baris dan revisi dijalankan aplikasi atas pilihan Pengawas (label "direvisi atas konfirmasi Pengawas"). Ini sama dengan tugas B yang direncanakan; masuk v9 (sisi agen) dan build 4 (sisi aplikasi), cadangan: roadmap bila waktu tidak cukup. Kasus uji baru K23.

- 2026-11-04 11:28 Keputusan Rany (label dan catatan): (e) ganti label: di daftar rencana "(ke-N)" -> "No. rencana N"; kolom "KE" di tabel -> "No."; di laporan Driver "ritase ke-N dari 4" -> "Ritase ke-N (normal 1-4, lembur 5-7)". AGENTS_v9 mendefinisikan "No. rencana N" = nomor urut baris rencana hari itu untuk pelapor, "Ritase ke-N" = hitungan ritase. (f) catatan "diinput dan disetujui oleh orang yang sama" hanya bila Pengawas menginput laporan atas nama Mandor/Driver DAN Pengawas yang sama kemudian menyetujuinya; ditulis oleh aplikasi saat Setuju (bukan agen).

- 2026-11-04 12:20 Temuan uji langkah 16 (Rany): teks tempel diubah ("Sesuai" -> "Bagus") tanpa klik "Baca hasil dari teks" tetap tersimpan, karena simpanHasilAgen() membaca dropdown th_/tk_, bukan textarea; textarea hanya disimpan sebagai arsip (l.hasil.mentah) -> arsip tidak sama dengan Tanda tersimpan. Perbaikan build 4: bila teks berubah sejak Baca terakhir, baca ulang otomatis atau tolak dengan pesan. Kasus uji: edit teks lalu Baca (harus merah), lalu Simpan (harus ditolak).
- Saldo 547 (11.38). Aturan H+1 laporan dan rencana selambatnya hari yang sama: menunggu 3 keputusan Rany (terlambat: tolak/tandai; rencana terlambat; batas jam dan zona).

- 2026-11-04 13:45 Uji K24 (teruskan catatan Pengawas ke Mandor): alur aplikasi DIKEMBALIKAN KE AGEN berfungsi. v8 tidak punya aturan untuk paket "teruskan catatan" -> v9 butir N. Build 4: blok data paket teruskan harus memuat Area/Zona dan label "Alasan Pengawas". Tambahan set-uji: K24 (teruskan catatan, draf saja, alasan apa adanya).

- 2026-11-04 14:20 Hasil uji "teruskan catatan ke Mandor" (v8, jawaban jam 13.50): LULUS isi (draf saja, alasan apa adanya, laporan yang sama, ringkasan data, foto tidak diketahui, tidak mengirim, tidak mengubah status). 6 celah dicatat agen (format pesan, paket tanpa rencana, tata cara revisi laporan yang sama, Temuan vs alasan pengembalian, profil usaha, kewenangan penerusan + audit log). v9 butir N diperluas (butir 7-9) untuk menutupnya. Prompt v9 belum dijalankan (menunggu Rany).

- 2026-11-04 14:25 Temuan UX (Rany, login Bagus): tombol "Perbaiki laporan ini" hanya ada di kartu C "Dikembalikan Pengawas" di tab Agen (paling bawah); di tab Lapor "Laporan saya/terbaru" tidak ada aksi, sehingga Mandor tidak menemukannya. Build 4: tombol Perbaiki + catatan Pengawas di tab Lapor dan Rencana Saya; lencana "Lapor (1)" bila ada yang dikembalikan; tab Agen disederhanakan/disembunyikan untuk Mandor dan Driver; tombol "teruskan catatan ke agen" hanya untuk Pengawas; kotak "Tempel pesan dari agen" + "Teruskan ke Mandor" (pesan disusun agen, diteruskan Pengawas, tercatat di Riwayat dan Audit Log).

- 2026-11-04 14:30 DISETUJUI Rany (build 4): kotak "Tempel pesan dari agen" + tombol "Teruskan ke Mandor" di kartu Dikembalikan. Pengawas yang menempelkan draf agen di aplikasi (bukan agen, bukan WhatsApp); Mandor membaca catatan Pengawas asli + pesan "disusun agen, diteruskan oleh Pengawas"; tercatat di Riwayat dan Audit Log.

## 2026-11-04 (siang) — temuan Jalur 1 langkah 20 (Bagus)
- Tombol "Perbaiki laporan ini": diuji ulang di luar WorkBuddy (Playwright, laporan DIKEMBALIKAN, login Bagus) — tombol bekerja, formulir muncul. Keluhan "tidak bisa diklik" belum terbukti; dugaan: formulir di bawah kartu / halaman melompat. Menunggu screenshot Rany.
- Build 4: setelah klik "Perbaiki", scroll otomatis ke formulir.
- Build 4: tab Agen hanya untuk Pengawas (Mandor/Driver tidak melihatnya); "Perbaiki laporan ini" + catatan Pengawas pindah ke tab Lapor; status/progres di Rencana Saya.
- Laporan ganda (kegiatan+tanggal sama) via form Lapor masih bisa dibuat -> item sudah ada: nonaktifkan item yang sudah dilaporkan kecuali yang dikembalikan, plus peringatan.

## 2026-11-04 14:30 — KOREKSI PRIORITAS (Rany): kesalahan fatal peran/menu
- Mandor/Driver TIDAK berinteraksi dengan agen sama sekali -> tab "Agen" DIHAPUS untuk Mandor/Driver (bukan sekadar disederhanakan). Menggantikan catatan 13:xx "sembunyikan/sederhanakan".
- Tombol "Perbaiki laporan ini" + catatan Pengawas + badge "Lapor (1)" ada di tab LAPOR (Mandor/Driver). Status/progres + tombol Lapor di Rencana Saya.
- Tab Agen = Pengawas saja (jembatan WorkBuddy, Tempel pesan dari agen, Teruskan ke Mandor).
- Jalur 1 langkah 20 = TEMUAN (gagal): di build sekarang Mandor tidak punya jalur perbaikan di menunya sendiri. Kandidat "uji gagal lalu diperbaiki" untuk demo.
- Kesalahan saya: mengarahkan Rany mencari tombol di tab Agen saat login Bagus. Selalu cek peran + menu sebelum menjelaskan.

## 2026-11-04 14:35 — KOREKSI 2 (Rany)
- Menu Pengawas TIDAK berubah: Rencana Mingguan, Lapor, Agen, Plan vs Realisasi, Riwayat, Master Data, Audit Log. Tidak ada tab "Tinjauan" (saya salah menulisnya). Setuju/Tidak setuju tetap di Plan vs Realisasi.
- Usulan Rany (bacaan saya, menunggu konfirmasi): langkah "agen menyusun pesan untuk Mandor" tidak perlu karena isinya sama dengan catatan Pengawas. Alur: Pengawas "Tidak setuju"+alasan -> alasan tampil langsung ke Mandor di tab Lapor -> Mandor "Perbaiki laporan ini" -> laporan sama masuk antrean agen.
- Bila dikonfirmasi: GUGUR tombol "teruskan-agen", kotak "Tempel pesan dari agen", "Teruskan ke Mandor", dan butir N (+terkait) di prompt_AGENTS_v9. Agen hanya 1 tugas: bandingkan laporan vs rencana.
- Tab Agen Mandor/Driver tetap dihapus (koreksi 14:30 berlaku).

## 2026-11-04 14:50 — Dokumen rancang dibuat (BRD+FSD+TSD, 1 doc)
- https://claude.ai/artifact/U5hnH3fmzq1nQ83K9KMmqd — draf, menunggu persetujuan Rany. Berisi diagram alur (3 jalur) + arsitektur, matriks peran-menu, status, daftar selisih build 4.
- Keputusan terbuka (bagian 4.1): input atas nama Mandor; menu/hak Admin; hapus langkah "agen susun pesan untuk Mandor"; aturan zona & lembur Driver.
- Build 4 dan AGENTS v9 HANYA disusun dari dokumen ini setelah disetujui.

## 2026-11-04 16:30 — alur 7 langkah (Rany) + rename menu
- Alur resmi: 1 Master Data (Admin/Pengawas) -> 2 Rencana Kerja (Pengawas, paling lambat H) -> 3 Lapor kegiatan (Mandor/Driver, paling lambat H+1) -> 4 Review via agen (Pengawas: salin perintah, tempel di WorkBuddy) -> 5 Agen bandingkan Rencana vs Realisasi, feedback ke Pengawas -> 6 Pengawas review feedback, beri catatan, tempel hasil di menu Agen -> 7 Approval di menu Rencana vs Realisasi: Setuju = CLOSED; Tidak setuju = Dikembalikan, masuk menu Mandor berstatus Dikembalikan -> Mandor perbaiki laporan sama -> ulang dari 4.
- RENAME (diminta Rany sebelumnya, LUPA dicatat): menu & judul Excel "Plan vs Realisasi" -> "Rencana vs Realisasi" sesuai template Excel Rany. Di papan3.html masih 10 kemunculan "Plan vs Realisasi" (+ teks di AGENTS/paket, cek). Masuk build 4.
- Diagram di dokumen rancang diganti ke swimlane vertikal 7 langkah.

## 2026-11-04 16:45 — Rekap mingguan Admin (keputusan Rany)
- Admin butuh rekap per minggu sbg dasar penggajian. Ada di AGENTS v8 Bagian 8 (mode berkas), TIDAK ada di aplikasi v3.
- KEPUTUSAN: masuk RANCANGAN saja (dokumen bagian 2.6), diperagakan di demo lewat MODE BERKAS. TIDAK masuk build 4. Menu "Rekap Mingguan" Admin = setelah build 4.
- Menu Admin (asumsi, tunggu konfirmasi): Master Data, Rekap Mingguan, Audit Log.
- Demo: siapkan skenario rekap mode berkas (data periode Sabtu-Jumat, hanya yang Disetujui dihitung, Belum Final, penolakan permintaan hitung gaji).

## 2026-11-04 16:50 — KOREKSI: Rekap Mingguan MASUK build 4 (aplikasi)
- Membatalkan catatan 16:45. Rekap Mingguan = menu Admin di aplikasi build 4 + aturan agen mode aplikasi di AGENTS v9 (butir baru, mis. O). Usulan urutan: dikerjakan paling akhir di build 4.
- Timeline Rany: sampai 18:00 review BRD/FSD -> build 4 di WorkBuddy (paralel susun ulang skenario uji) -> uji malam ini/besok pagi -> rekam Kamis.
- Usul Rany: uji dari chat yang sudah punya riwayat agar WorkBuddy tidak setup ulang. Tanggapan saya: build 4 = lanjut di chat tempat v3 dibangun; uji agen = satu chat khusus per versi AGENTS, kasus tercatat per pesan.

## 2026-11-04 16:55 — Menu REPORT (Rany): Pengawas + Admin, mingguan & bulanan, untuk klien
- Menu "Report" ada di Pengawas dan Admin; report per minggu dan per bulan (untuk laporan ke klien). Menggantikan "Rekap Mingguan hanya Admin".
- Dua jenis (ASUMSI, tunggu konfirmasi): (a) Laporan klien = matriks Rencana vs Realisasi bulanan per Area/Mandor (template Excel Rany, AGENTS v8 Bagian 10; 31 kolom tanggal, baris Rencana/Realisasi, Total Aktivitas); (b) Rekap penggajian Admin (AGENTS v8 Bagian 8, periode Sabtu-Jumat, 3 sheet).
- Aplikasi v3 hanya punya Excel datar 10 kolom, BUKAN matriks -> build 4 harus membuat matriks.
- Keputusan desain terbuka: angka dihitung aplikasi (deterministik) dan agen mereview/memberi catatan, ATAU agen menyusun. Saran: aplikasi hitung angka (aturan agen sendiri melarang mengarang angka; jembatan salin-tempel hanya teks).

## 2026-11-04 17:05 — Desain Report DISETUJUI Rany (hibrida)
- Aplikasi hitung angka acuan dari laporan CLOSED -> paket -> agen hitung sendiri dari data mentah + cocokkan + tandai selisih/belum final/susulan/libur/kejanggalan + catatan ringkas klien (jawaban = tabel teks format tetap) -> tempel di aplikasi: baca + pratinjau -> aplikasi buat Excel (matriks klien / rekap gaji) -> Admin/Pengawas verifikasi & approve -> Audit Log.
- Item build 4 baru (terbesar): menu Report (Pengawas+Admin), pembuat matriks Excel (31 kolom, kuning/abu, Total), pembaca tabel jawaban agen, paket report, approval + audit.
- AGENTS v9: butir baru tugas Report mode aplikasi (format jawaban tabel, aturan hitung ulang & selisih); butir N tetap gugur.
- Excel v3 10 kolom: Tanggal, Area, Zona, Orang, Peran, Kendaraan, Kegiatan, Ritase, Status, Tanda (+ kolom 11 Catatan agen, target).

## 2026-11-04 17:15 — Rencana Saya & "belum dilaporkan" (pertanyaan Rany)
- Fakta v3: Rencana Saya = SATU tanggal sekali (bawaan hari ini; pilih tanggal + Tampilkan), tanpa kolom status. Kegiatan belum dilaporkan hanya terlihat Pengawas di Rencana vs Realisasi ("Belum ada laporan" per baris rencana, per tanggal). Mandor/Driver tidak melihatnya di mana pun. Agen tidak diberi daftar rencana tanpa laporan (paket per laporan).
- Usulan build 4: Rencana Saya pilihan Hari ini/Minggu ini + kolom status (Belum dilaporkan/Menunggu/Disetujui/Dikembalikan) + tombol Lapor.
- Usulan AGENTS v9 + build 4: paket review memuat rencana hari itu termasuk yang belum ada laporan; agen jawab baris `Belum dilaporkan | ID rencana | catatan`; sampai H+1 23.59 WIB = Belum dilaporkan, sesudahnya Tidak dilaporkan + tandai ke Pengawas. Parser perlu tipe baris baru.

## 2026-11-04 17:20 — DISETUJUI Rany: agen memberi tahu Pengawas kegiatan belum dikerjakan/dilaporkan
- Rencana Saya (Hari ini/Minggu ini + kolom status + tombol Lapor) = keputusan. Baris `Belum dilaporkan` dari agen = keputusan; dikelompokkan per Mandor dan per Area; H+1 23.59 WIB -> Tidak dilaporkan + tandai ke Pengawas. Peran utama agen membantu Pengawas.
- Masuk AGENTS v9 (butir baru) dan build 4 (paket + parser tipe baris baru + tampilan di Agen dan Rencana vs Realisasi).

## 2026-11-04 17:30 — Pilihan B audit log + revisi prompt_AGENTS_v9.md
- DISETUJUI Rany: agen tidak menulis apa pun (termasuk audit log) tanpa persetujuan. Mode berkas: baris audit diusulkan di layar konfirmasi / "Catatan audit yang diusulkan"; mode aplikasi: aplikasi yang mencatat. Alasan: kriteria panitia "tidak ada tindakan sebelum disetujui" (kegagalan kritis -> skor Responsible AI maks 5/10).
- prompt_AGENTS_v9.md direvisi (cadangan: prompt_AGENTS_v9_sebelum-revisi-17.md): butir N lama (teruskan catatan) DIBUANG; butir baru N = audit log tanpa pengecualian, O = Belum dilaporkan (blok RENCANA HARI INI, Tanda ke-5, [Lewat batas] setelah H+1 23.59, ringkasan per Mandor/Area), P = Report (format jawaban REKAP/MATRIKS/BELUM FINAL/SELISIH/CATATAN KLIEN, dibagi dengan build 4). Total butir A-P. Tanda jawaban jadi 5.
- Catatan: "Tidak dilaporkan" setelah H+1 diwujudkan sebagai awalan [Lewat batas] pada Tanda Belum dilaporkan (agar parser tetap 5 Tanda).
- Format jawaban Report HARUS sama di v9 dan prompt build 4. Belum ditinjau Rany.
- Belum tercakup mode aplikasi: Jumat/libur/WITA (aplikasi hanya WIB) -> diperagakan di mode berkas.

## 2026-11-04 17:35 — dari kriteria panitia (disetujui Rany)
- Diagram arsitektur: ditambah trust boundary (zona putus-putus, teks hanya lewat Pengawas, isi laporan Mandor/Driver = data tak tepercaya) dan trade-off salin-tempel vs API. SELESAI.
- Kasus uji DITAMBAH SAAT PENGUJIAN (jangan lupa): (1) nama ambigu (dua orang bernama sama -> agen tanya yang mana), (2) instruksi tersisip di keterangan/dokumen (agen abaikan + beri tahu), (3) Jumat/libur/WITA (mode berkas), (4) SATU kegagalan nyata yang kita perbaiki, direkam untuk video.
- Masih harus dikonfirmasi Rany: PDF panduan mencantumkan batas pengumpulan 1 Nov 2026 (rencana kita 7 Nov) -> pastikan pengumuman perpanjangan.
- Belum ada rencana: source code publik / ekspor workflow WorkBuddy (wajib), deskripsi dengan nilai terukur, lembar akuntabilitas, blurb <=10 kata.

## 2026-11-04 18:30 — Tinjauan Pengawas (keputusan Rany)
- v3: Rencana vs Realisasi hanya per SATU tanggal; Setuju/Tidak setuju per laporan; Excel juga per tanggal.
- Build 4: filter rentang tanggal (bawaan kemarin-hari ini) + filter status (bawaan Menunggu tinjauan & Menunggu konfirmasi); CENTANG beberapa laporan -> Setuju sekaligus. Tidak setuju tetap satu per satu (alasan wajib). Audit Log satu baris per laporan. Prioritas tinggi (aturan H+1).
- Komponen rentang tanggal dipakai bersama menu Report.
- Dokumen rancang BRD/FSD: Rany menyatakan sesuai (18:25).

- 2026-11-04 18:40 — Prompt build 4a & 4b ditulis (`prompts/prompt_build4a.md`, `prompt_build4b.md`). Asumsi: menu Admin = Rencana Mingguan, Laporan, Rencana vs Realisasi (lihat), Master Data, Audit Log (+ Report di 4b); "Minggu ini" = Sabtu-Jumat; Lembur & Di luar rencana dikecualikan dari Setuju massal. Menunggu koreksi Rany.
- 2026-11-04 18:55 — Kalimat standar baris pertama SEMUA perintah salin: "Semua balasan kepada saya dalam bahasa Indonesia." (4a butir 7a, 4b paket Report). v3 belum memuatnya. Verifikasi setelah build: 3 jalur salin.

- 2026-11-04 19:25 — [Keputusan] Panitia (grup WA, via Alya Fitri/Tencent, 16:13): "bisa skip part ini, bisa langsung pakai dataset sendiri". Pengujian memakai data mock buatan sendiri; tidak menunggu dataset resmi. Tulis di pengungkapan/deskripsi: dataset sendiri dengan izin panitia (tangkapan layar WA disimpan sebagai bukti).
- 2026-11-04 19:25 — [Keputusan] Setuju urutan: build 4a/4b -> verifikasi -> rapikan tampilan (landing + kartu peran, di luar WorkBuddy, dicatat di pengungkapan; logika tidak diubah) -> tautan hidup GitHub Pages. Foto orang tidak dipakai (inisial/ilustrasi).

- 2026-11-04 19:41 — [Keputusan] Rany: perapian tampilan (landing page, kartu peran) dikerjakan DI WorkBuddy lewat prompt dari saya (bonus karya terbukti dibangun di WorkBuddy; aturan panitia 2 Nov: logika orkestrasi harus dibangun/dijalankan di WorkBuddy). Tidak diubah kodenya sendiri di luar WorkBuddy. Pertanyaan ke grup dipersingkat, merujuk jawaban panitia 2 Nov.
- 2026-11-04 21:45 — Build 4a (prompt tunggal) dihentikan Rany di menit ke-14, belum ada v4; terpakai ±42 kredit (535->493). Perkiraan saya (20-40) terlalu rendah. Diganti prompt terpisah 4a-1 (butir 1-5, v3->v4a1), 4a-2 (butir 6-7, v4a1->v4), 4b (v4->v5), semua dengan aturan EDIT TERARAH, bukan tulis ulang.

- 2026-11-04 23:10 — Build 4a-1 DIPERIKSA (uji otomatis jsdom di luar WorkBuddy, `scratchpad/app4/t4a1.js`, `t2.js`): butir 1-5 LULUS (menu 5 peran, rename, tab Lapor+Perbaiki ID sama, dropdown nonaktif+peringatan, Rencana Saya hari/minggu+status+tombol, badge Lapor (n), scroll ke form). Kredit 4a-1 = 34 (493->459), ±1 jam. Belum diperiksa: tampilan visual di browser nyata. Catatan sisa: sheet Excel bernama "Rencana vs Realisasi-Rencana/-Realisasi" (rapikan nanti); teks lama "ritase ke-8 ditolak" masih dari v3 (selaraskan dg aturan >7 = Perlu pengajuan di 4a-2/4b).
- 2026-11-04 23:20 — Perbaikan kecil v4a1 (nama lembar Excel; teks ritase >7) digabung ke prompt 4a-2 sebagai butir 8 (keputusan Rany).

- 2026-11-05 07:30 — Build 4a-2 -> v4 DIPERIKSA (jsdom, `scratchpad/app4/t4.js`, `t5.js`): 33 uji LULUS. Kalimat wajib baris 1 di semua jalur salin (teksPerintah, teksPerintahBanyak, salin(), tombol salin semua); blok DATA MASTER ZONA + RENCANA HARI INI; ID fiktif; Teruskan dihapus; review: rentang kemarin–hari ini, status bawaan MENUNGGU, centang massal (Lembur/Di luar rencana nonaktif), Audit 1 baris/laporan, Tidak setuju wajib catatan, Admin tanpa tombol; parser 5 Tanda + Belum dilaporkan terkelompok + tolak simpan bila teks berubah; lencana; Excel kolom ke-11, lembar "Rencana"/"Realisasi"; teks ritase >7. Kredit 4a-2 ±25 (459->433,85). Penyimpangan kecil diterima: filter status = satu pilihan gabungan (bukan multi-pilih); Perlu konfirmasi -> MENUNGGU KONFIRMASI PENGAWAS (tafsiran WorkBuddy). Belum diperiksa: tampilan visual di browser nyata.
- 2026-11-05 07:10 — Prompt 4b dipecah: 4b-1 (v4->v5a: menu Report, periode, angka acuan, perintah ke agen) dan 4b-2 (v5a->v5: baca jawaban, persetujuan, Excel). Hasil pemeriksaan v4: tidak ada perbaikan wajib; 2 penyimpangan kecil diterima, jadi tidak ada tambahan di 4b.
- 2026-11-05 08:05 — v5a (4b-1) DIPERIKSA (t6.js): menu Report hanya Pengawas+Admin LULUS; periode, BELUM FINAL, ritase Driver, realisasi per tanggal, kalimat wajib LULUS. 2 TEMUAN -> masuk prompt 4b-2 butir 0: (a) hari Lembur Mandor (rencana.lembur) terhitung 0 — salah, dasar penggajian; (b) baris catatan pengembang 'Tahap 4b-1...' bocor ke perintah agen.
- 2026-11-05 14:10 — Cadangan: prompt_build4b3.md (HANYA Excel, v5->v6) bila 4b-2 tidak sempat membuat Excel. 4b-2 berjalan sejak ±12.15 dan jam 14.00 masih di butir 0a (membaca berkas berulang).
- 2026-11-05 14:45 — 4b-2 dihentikan Rany (Thinking macet >1 jam, belum ada hasil). Keputusan usulan: prioritas uji agen + AGENTS v9 dulu; menu Report cukup v5a + perbaikan mini (prompt_build4b2mini.md: hari Lembur Mandor + hapus baris dev); parser jawaban/persetujuan/Excel Report = keterbatasan/roadmap kecuali sisa waktu. Catatan: saldo WorkBuddy tidak turun selama tugas berjalan (dipotong saat selesai/dihentikan).
- 2026-11-05 15:00 — Prompt AGENTS v9 dipecah 4 langkah di chat yang sama (permintaan Rany; panitia juga menyarankan prompt sedikit-sedikit): _1 butir A-E, _2 F-L, _3 N,O,P, _4 M + CATATAN_VERSI + berkas akhir. Lampiran hanya di langkah 1.
- 2026-11-05 15:20 — v5 (hasil 4b-2 yang dihentikan, file tetap tersimpan) DIPERIKSA: butir 0a LULUS (Lembur Mandor=1), baris dev dihapus dari perintah agen; parser REKAP/MATRIKS/BELUM FINAL/SELISIH/CATATAN KLIEN/SUMBER, kata kunci asing merah, SELISIH berwarna, persetujuan wajib centang + 1 baris Audit, Unduh aktif hanya setelah setuju, Excel Rekap 3 lembar tanpa kolom gaji, Matriks 1 lembar (kuning/abu/Total Aktivitas/CATATAN KLIEN) LULUS; regresi 4a lulus. Sisa: teks dev 'Tahap 4b-1...' masih tampil di layar (baris ~3296). Kredit 4b-2 = 27 (409->382). Prompt 4b3 tidak diperlukan.
- 2026-11-05 15:10 — prompt_build4b2sisa.md (v5->v5b): hapus teks pengembang di layar Report + cari sisa. Jalankan SETELAH AGENTS v9 (opsional, murah).
- 17:45 v9 dibuat di luar WorkBuddy (lebih lengkap dari file WorkBuddy yang berhenti di butir 17, tanpa N/O/P); dipakai. Catat di pengungkapan.
- 17:50 uji agen v9: langkah 1 (cek pemahaman, prompt kecil) -> prompts/uji_agen_v9_langkah1.md. Catat: WorkBuddy kesulitan prompt berat (sesi v9 macet 15.08-17.35). Ulang uji gagal v8: no 6,19,20,21,23,5.
- 19:25 v9 final = hasil WorkBuddy (A-L sesi 1; N1,N2,O,P prompt kecil; saldo 352->343) + perapian header di luar WB. Versi buatan Claude (v9_luar) jadi cadangan/pembanding.
- 19:40 UAT aplikasi v5 (45 langkah) dibuat: tests/UAT-aplikasi-v5.xlsx; dikerjakan sebelum uji agen (Jalur 1).
- 21:45 UAT v2: urutan diperbaiki (Agen sebelum Rencana vs Realisasi). Pemetaan nomor lama->baru: 27-33 -> 21-27; 21-26 -> 28-33. File tests/UAT-aplikasi-v5_v2.xlsx

## 2026-11-05 malam — temuan uji (belum diperbaiki, keputusan setelah semua uji selesai)
- FOTO: aplikasi hanya menyimpan NAMA berkas; isi gambar tidak disimpan dan tidak bisa dilihat Pengawas/Pemilik/Admin. Batasan desain (satu HTML + localStorage ±5 MB). Rencana lanjutan: simpan foto (lihat usulan struktur di bawah). Permintaan Rany: posisi lebih kuat bila foto bisa diakses.
  Usulan struktur (RANCANGAN, belum dibangun): penyimpanan objek terpisah (opsi: Google Apps Script+Drive, atau Tencent Cloud COS, atau IndexedDB lokal bila tetap offline); aplikasi hanya menyimpan referensi per foto {nama, hash sha256, ukuran, waktu_unggah, pengunggah, lokasi_berkas}; jalur berkas /laporan/{tanggal}/{id_laporan}/foto{n}; kompres sisi klien (±1280 px); hak lihat per peran; Audit Log "lihat foto"; hash sama = foto dobel (lebih kuat dari nama berkas). Konsekuensi: butuh layanan luar -> keluar dari "satu berkas tanpa internet"; data foto asli klien = isu privasi (tetap data tiruan untuk lomba).
- BELUM DILAPORKAN salah positif: paket tidak menandai baris rencana yang SUDAH punya laporan; agen menandai Anti Hama (No. 5) sebagai Belum dilaporkan padahal CLOSED (chat sama, agen memakai ingatan chat). Aplikasi menerima baris itu tanpa mencocokkan dengan datanya. -> kandidat pasangan "gagal lalu diperbaiki": penanda "SUDAH ADA LAPORAN" per baris di paket + pencocokan di aplikasi.
- ID rencana ganda ("a / b") pada Perlu konfirmasi diterima aplikasi tanpa peringatan.
- Tombol Setuju massal berada di kartu paling atas, jauh dari kotak centang (sulit ditemukan).
- Kartu Perlu konfirmasi (zona kosong) memakai kalimat "Tambahkan kegiatan ... ke rencana" dengan Setuju/Tolak; tidak cocok dengan pertanyaan agen (seluruh Area atau zona tertentu).
- Form: satu laporan hanya satu zona (kerja lintas zona = keterangan atau dua laporan). Nama foto dobel diterima. Teks AGENTS_v8 masih ada di paket/banner. "(keterangan wajib)" tampil ganda di daftar aktivitas Driver.
- Alur dikembalikan (Tolak -> Perbaiki -> kirim ulang): lulus; ID laporan sama, Riwayat lengkap.
- REPORT (Matriks klien, 05/11): kolom "Belum final" hanya menghitung laporan yang ada tetapi belum CLOSED (0 = benar). Kegiatan rencana yang TIDAK PERNAH dilaporkan tidak muncul di Report (tampil 9 rencana vs 6 realisasi tanpa penjelasan selisih 3). Permintaan Rany: tambahkan informasi "Belum dilaporkan" di Report (kolom/daftar per tanggal dan per orang; ikut ke teks paket Report agar agen tidak menghitung sendiri). UAT langkah 40 tetap lulus menurut lembar; ini temuan tambahan.
- DUGAAN (belum dibuktikan): Setuju pada kartu Perlu konfirmasi menambah baris rencana baru (rencana 05/11 jadi 9 baris, Pemangkasan No. 3 bisa tertinggal kosong). Menunggu cek Rencana Saya Slamet dan Rencana vs Realisasi.
- TERBUKTI (23:53): Setuju pada kartu "Perlu konfirmasi" (Pemangkasan zona kosong) menambah baris rencana baru No. 7, padahal Pemangkasan No. 3 sudah ada. Laporan terhubung ke No. 7; No. 3 tetap "Belum dilaporkan" (salah). Daftar Belum dilaporkan jadi 3 (No. 2, 3, 4) seharusnya 2; rencana 05/11 jadi 9 baris; Report Matriks 9 rencana vs 6 realisasi. Penyebab: Setuju bermakna "tambahkan ke rencana" (aturan Di luar rencana) dipakai juga untuk Perlu konfirmasi. Usulan perbaikan: kartu Perlu konfirmasi -> Pengawas pilih rencana yang sudah ada / tambah baru / tolak. Kandidat utama pasangan "gagal lalu diperbaiki" untuk demo.
- Catatan: daftar Belum dilaporkan dihitung aplikasi dari data sendiri; baris Belum dilaporkan salah dari agen (Anti Hama) tidak ikut tersimpan setelah Simpan.
- REPORT AGEN (Matriks klien, 05/11 00:02): pratinjau 18 baris terbaca, 0 merah; saldo 363 -> 359 (-4), model Auto, chat sama, paket tanpa baris aturan (tidak ditambah Rany).
  Lulus: angka per orang & realisasi cocok, tanpa gaji, 1 SUMBER, anomali Samsul/Jumat terdeteksi.
  Gagal sebagian: SELISIH rencana 9|9 dan 1|1 "tidak ada selisih" = angka acuan dibandingkan dengan dirinya (rencana tidak bisa dihitung dari data mentah; instruksi 1 dilanggar). CATATAN KLIEN tidak menyebut 3 kegiatan belum dilaporkan; memuat anomali internal.
  Aplikasi: tabel perbandingan hanya untuk baris REKAP ("Tidak ada baris REKAP untuk dibandingkan"); baris MATRIKS/SELISIH tidak dibandingkan dengan angka acuan -> penjaga tidak bekerja pada Matriks klien.
  Paket Report: tidak merujuk berkas aturan; kolom "Tanda" hanya penanda (bukan Tanda agen); laporan yang ditambahkan ke rencana lewat Setuju tampil "DI LUAR RENCANA" + "Di luar rencana: tidak" tanpa penjelasan; tidak ada daftar rencana/belum dilaporkan.
  Agen memakai ingatan chat (menyebut blok rencana sebelumnya).
- UJI NEGATIF REPORT (06/11 00:09): jawaban agen Matriks klien (tanpa baris REKAP) ditempel ke Report Rekap penggajian, disetujui, Excel diunduh (Report_RekapPenggajian_2026-11-06_1.xlsx).
  Temuan: (a) Rekap per orang: kolom agen "-" tetapi Selisih "tidak ada" (kepastian palsu); (b) Rincian per tanggal menjumlahkan baris MATRIKS termasuk baris "(total tanggal)" -> Rencana (agen) 15 dan Realisasi (agen) 12 vs acuan 9 dan 6, tanpa tanda selisih; (c) pratinjau "Tidak ada baris REKAP untuk dibandingkan" tetapi Setujui + Unduh Excel tetap jalan. Usulan: tolak Setujui bila jenis Rekap tidak punya baris REKAP; tulis "tidak ada jawaban agen" bukan "tidak ada selisih"; jangan jumlahkan baris total; bandingkan juga angka MATRIKS dengan acuan.
- Catatan paket: paket Report pertama (00:06) masih bertuliskan "Jenis report : Matriks klien" walau Rany ingin Rekap penggajian (dibuat oleh Dewi/Admin); perlu pastikan Tampilkan menerapkan jenis sebelum menyalin.
- TEMUAN RANY (06/11 00:12): saat jenis Report diganti ke Rekap penggajian, jawaban agen lama (Matriks klien) dan pratinjaunya tetap terbaca. Penyebab (kode ~L3304): state jawaban sengaja dipisah dari U.ui.rep agar "Tampilkan" tidak menghapusnya; pratinjau tidak dibaca ulang untuk jenis baru; persetujuan terikat awal|akhir|jenis|teks tetapi Setujui tetap bisa ditekan karena teks lama masih valid. Usulan: simpan jawaban per jenis+periode atau hapus saat jenis/periode berubah; peringatan; wajib baris REKAP untuk Rekap penggajian.
- [WAJIB DIPERBAIKI — prioritas tinggi] (Rany, 06/11 00:14) Report: ganti jenis report atau periode HARUS mengosongkan kotak jawaban agen, pratinjau, centang "sudah saya periksa", dan persetujuan. Bukti tangkapan layar: jenis Rekap penggajian tetapi kotak masih berisi baris MATRIKS, pratinjau lama tampil, centang tetap, stempel "Disetujui oleh Dewi (Admin) ... Rekap penggajian" muncul memakai jawaban jenis lain. Risiko: persetujuan laporan penggajian dengan jawaban yang bukan miliknya. Perbaikan: reset state jawaban (U.ui.repAns) di handler rep-terapkan bila jenis/periode berubah; Rekap wajib baris REKAP sebelum bisa disetujui. Kandidat pasangan "gagal lalu diperbaiki" untuk demo (selain Setuju Perlu konfirmasi menambah baris rencana).
- STATUS UJI (06/11 00:14): uji agen Report Rekap penggajian (baris REKAP, pratinjau perbandingan, uji ubah-satu-angka merah) DITUNDA sampai perbaikan reset state Report; ulangi setelah perbaikan. Uji Matriks klien: selesai (lulus dengan temuan).
- UJI AGEN REKAP PENGGAJIAN (06/11 00:16, chat sama, tanpa baris aturan, Auto, saldo 359 -> 354 = -5, 24 dtk): jawaban berisi 3 baris REKAP (Bagus 1|tidak berlaku|0|0; Samsul 1|1|0|0; Slamet 1|tidak berlaku|0|0), 9 baris SELISIH per orang (tanpa klaim rencana/realisasi melingkar seperti Matriks), CATATAN KLIEN, 1 SUMBER, tanpa gaji, anomali dilaporkan, celah aturan dicatat. Hasil: lulus. Pemeriksaan pratinjau aplikasi dan uji ubah-satu-angka menyusul.
- TEMUAN RANY (06/11 00:19): pratinjau Rekap menampilkan baris "Ritase (Driver)" untuk Mandor (Bagus, Slamet) dengan "-" dan "tidak bisa dibandingkan". Penyebab (kode ~L3363): perulangan membandingkan 3 item (hari kerja, ritase, lembur) untuk SETIAP orang tanpa melihat peran. Usulan: baris ritase hanya untuk Driver; Mandor tulis "tidak berlaku". Tambahan: agen menulis baris SELISIH "ritase Bagus/Slamet | tidak berlaku" (noise, ikut hitungan "Jumlah SELISIH: 9") -> v9.1: jangan tulis SELISIH untuk item tidak berlaku.
- Pratinjau Rekap setelah Baca hasil: tabel perbandingan 3 orang hijau (hari kerja & lembur sama), ritase Mandor "tidak bisa dibandingkan", 14 baris dipakai, 0 merah; centang & Setujui kembali nonaktif setelah Baca (reset persetujuan bekerja).
- TEMUAN RANY (06/11 00:23, UX): pratinjau Report terlalu rapat/padat untuk Pengawas (teks kecil, banyak baris mentah "Baris terbaca", angka sulit dibaca); mengubah angka di teks mentah membingungkan. Usulan: tampilkan tabel perbandingan lebih besar dan paling atas, lipat daftar "Baris terbaca" (tombol buka/tutup), tandai hanya baris merah dengan ringkasan "1 selisih ditemukan", huruf lebih besar. Catatan uji: uji ubah-angka dilakukan dengan 1 baris REKAP uji (bukan edit blob panjang).
- EXCEL REKAP PENGGAJIAN (Report_RekapPenggajian_2026-11-06_2.xlsx, 06/11 00:25): lulus. Kolom agen terisi dari baris REKAP (Bagus 1|-|0|0, Samsul 1|1|0|0, Slamet 1|-|0|0), Selisih "tidak ada", Rincian per tanggal tanpa angka agen (tidak ada hitung ganda karena tidak ada baris MATRIKS), CATATAN KLIEN dan SUMBER utuh, tanpa gaji.
  TEMUAN: "JUMLAH SELISIH 9" (Excel) dan stempel persetujuan "jumlah SELISIH: 9" menghitung BARIS SELISIH dari agen walau semuanya "tidak ada selisih"; selisih sebenarnya 0 (pratinjau menulis "item perbandingan berselisih: 0"). Menyesatkan: pembaca mengira 9 selisih. Kode: jumlahSelisih = item berselisih + out.selisih.length. Perbaiki: hitung hanya baris yang benar-benar berselisih. Sama pada Excel Matriks (8). Duplikasi: ritase Mandor muncul di SELISIH agen dan di PERBANDINGAN "tidak bisa dibandingkan".
- UJI UBAH ANGKA (00:24): 1 baris REKAP Slamet hari kerja 2 -> baris merah SELISIH, jumlah 1. Lulus (bukti penjaga angka REKAP bekerja).
- AUDIT LOG (tangkapan layar 06/11 00:27, bagian atas): baris Masuk, Salin perintah Report, Setujui report tercatat dengan waktu WIB, peran, aktor, objek, nilai sebelum -> sesudah; sumber semua "Aplikasi" (tidak ada aktor agen). Bukti defect: 00:08 Dewi menyetujui Rekap penggajian "jumlah SELISIH: 8" (jawaban Matriks lama), lalu 00:20 dan 00:25 "jumlah SELISIH: 9".
  TEMUAN: (a) dua baris "Setujui report" identik pada 00:03 (Hadi, Matriks klien) -> dobel klik atau pencatatan ganda; (b) Unduh Excel Report yang BERHASIL tidak tercatat (kode L3696+: hanya penolakan hak akses yang dicatat) — data penggajian keluar tanpa jejak; (c) "Baca hasil" Report tidak tercatat (tab Agen mencatat "Baca hasil dari teks"); (d) label "jumlah SELISIH: n" di catatan Audit Log sama menyesatkannya dengan Excel.
  Belum diperiksa: baris Tolak, Setuju (massal dan satuan), Perbaiki, Tambahkan kegiatan di luar rencana (sekitar 23:10-23:25).
