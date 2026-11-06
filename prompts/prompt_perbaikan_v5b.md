# Prompt perbaikan WorkBuddy — Jumat 6 Nov 2026
Dasar: PantauUsaha_Papan_v5.html (sha256 a68679000c3d…91377) + hasil UAT-aplikasi-v5.xlsx + temuan uji agen/Report malam 5–6 Nov.

## Cara pakai (baca dulu)
1. Satu prompt = satu tugas WorkBuddy. Tunggu selesai, UNDUH hasilnya, kirim ke Claude untuk diperiksa (diff + uji) SEBELUM prompt berikutnya. Jangan percaya "✅" WorkBuddy.
2. Setiap prompt memakai berkas hasil prompt sebelumnya (v5 → v5b → v5c …). Nama berkas ada di tiap prompt.
3. Tiap prompt P2 dst. sudah memuat permintaan berkas ZIP (berisi .html) + .txt; .html polos tidak bisa diunduh dari WorkBuddy. Ganti `[ISI JAM]` dengan jam WIB sebenarnya. Pakai chat BARU untuk tiap prompt bila bisa (agar tidak terbawa memori chat).
4. Batas 15 menit tanpa perubahan → hentikan, catat kasusnya.
5. Model: Auto 0.15x — catat saldo sebelum & sesudah tiap prompt.
6. Estimasi (perkiraan, bukan pengukuran): 5–15 menit dan sekitar 3–8 kredit per prompt.

Urutan: P1 → P2 → P3 → P4 → P5 → P6 → P7 → P8 (P8 = AGENTS, dikerjakan terakhir/di jalur agen).

---

## P1 — Report: state harus reset + validasi jenis (WAJIB)
Berkas masukan: PantauUsaha_Papan_v5.html → keluaran: PantauUsaha_Papan_v5b.html

```
Semua balasan kepada saya dalam bahasa Indonesia.
Waktu sekarang (WIB): Jumat, 6 November 2026, [ISI JAM]

Tugas: perbaikan TERARAH pada berkas PantauUsaha_Papan_v5.html. JANGAN menulis ulang berkas; ubah hanya yang disebut. Simpan hasil sebagai PantauUsaha_Papan_v5b.html (v5 jangan ditimpa). JANGAN menjalankan pengujian; cukup edit dan ringkas perubahan.

Masalah: di menu Report, bila jenis report atau periode diganti, jawaban agen lama (U.ui.repAns / stateJawabanReport) masih terbaca, dan Rekap penggajian bisa disetujui tanpa baris REKAP.

Perbaiki:
1. Pada handler "rep-terapkan" (sekitar baris 4095-4103) dan setiap kali Jenis report atau Periode berubah: kosongkan jawaban agen (U.ui.repAns), hasil baca, pratinjau, dan centang "sudah saya periksa". Tampilan kembali ke keadaan "belum ada jawaban agen".
2. Pada jawabanReportValid / tombol "Setujui report": 
   - jenis "Rekap penggajian" hanya valid bila ada minimal 1 baris REKAP;
   - jenis "Matriks klien" hanya valid bila ada minimal 1 baris MATRIKS;
   - bila tidak valid, tombol Setujui nonaktif dan tampil pesan jelas: "Jawaban agen tidak berisi baris REKAP/MATRIKS untuk jenis report ini."
3. Kunci persetujuan (kunciPersetujuanReport) tetap memakai awal|akhir|jenis|bacaTerakhir; jangan diubah.

Jangan mengubah hal lain. Di akhir tulis: daftar fungsi/baris yang diubah (maksimal 10 baris).
```

Verifikasi Claude: diff v5→v5b; uji pindah Matriks→Rekap (harus kosong); Rekap tanpa REKAP tidak bisa disetujui.

---

## P2 — Teks AGENTS_v8 → AGENTS_v9 + Report paket menyebut aturan
Berkas masukan: v5b → keluaran: v5c

```
Semua balasan kepada saya dalam bahasa Indonesia.
Waktu sekarang (WIB): Jumat, 6 November 2026, [ISI JAM]

Tugas: perbaikan TERARAH pada PantauUsaha_Papan_v5b.html → simpan sebagai PantauUsaha_Papan_v5c.html. JANGAN tulis ulang berkas. JANGAN menjalankan pengujian.

1. Ganti semua teks "AGENTS_v8" / "AGENTS_v8.md" menjadi "AGENTS_v9" / "AGENTS_v9.md" (cari: paket header sekitar baris 1893, "Lampiran" sekitar baris 2044 dan 2068, catatan banner sekitar baris 2348, dan kemunculan lain). Jangan ubah isi aturan AGENTS di dalam berkas.
2. Pada paket perintah Report (jenis Matriks dan Rekap), tambahkan di baris awal, tepat setelah baris "Waktu sekarang (WIB)": "Baca dan jadikan AGENTS_v9.md sebagai aturan, khususnya butir 18 (Belum dilaporkan) dan butir 19 (format Report)."
3. Hapus teks ganda "(keterangan wajib)" bila muncul dua kali di formulir yang sama (cukup satu).

Di akhir tulis daftar baris yang diubah.

Berkas hasil WAJIB langsung disediakan sebagai DUA berkas unduhan sekaligus, tanpa saya minta lagi: (1) .zip yang berisi berkas .html hasil; (2) salinan berekstensi .txt yang isinya IDENTIK karakter demi karakter dengan .html (nama sama). Jangan ubah isi saat menyalin/mengemas. Tulis ukuran kedua berkas (KB) di akhir.
```

Verifikasi Claude: grep "AGENTS_v8" harus 0 hasil; diff hanya teks.

---

## P3 — Report: angka SELISIH + Ritase hanya Driver
Berkas masukan: v5c → keluaran: v5d

```
Semua balasan kepada saya dalam bahasa Indonesia.
Waktu sekarang (WIB): Jumat, 6 November 2026, [ISI JAM]

Tugas: perbaikan TERARAH pada PantauUsaha_Papan_v5c.html → simpan sebagai PantauUsaha_Papan_v5d.html. JANGAN tulis ulang. JANGAN jalankan pengujian.

Pada logika pembandingan Report (loop banding sekitar baris 3363-3375, out.jumlahSelisih sekitar baris 3375, teks pratinjau sekitar baris 3459, Excel "JUMLAH SELISIH" sekitar baris 3683):
1. Baris "Ritase" hanya dibandingkan dan ditampilkan untuk orang berperan Driver. Untuk Mandor dan peran lain: tidak ada baris Ritase sama sekali (bukan "tidak berlaku").
2. "Jumlah SELISIH" = HANYA jumlah item yang angka agennya BERBEDA dari angka acuan aplikasi. Baris SELISIH dari agen yang menyatakan "tidak ada selisih" atau angka sama TIDAK dihitung.
3. Di pratinjau dan Excel ubah label menjadi "Jumlah item berselisih" dan tambahkan keterangan satu baris di bawahnya: "Angka 0 berarti semua angka agen sama dengan acuan aplikasi."
4. Di pratinjau, ganti istilah "Hari kerja" menjadi "Hari kerja (jumlah tanggal berbeda dengan laporan CLOSED)" pada judul kolom/baris pertama saja.

5. Teks ganda "(keterangan wajib)": nama kegiatan k13 di data master (sekitar baris 263) sudah memuat "(keterangan wajib)", lalu sekitar baris 1985 ditambahkan lagi. Hapus tambahan di baris 1985 hanya bila nama kegiatan sudah memuat teks itu (cek dengan indexOf), supaya tidak tampil dua kali.

Jangan ubah hal lain. Tulis daftar baris yang diubah di akhir.

Berkas hasil WAJIB langsung disediakan sebagai DUA berkas unduhan sekaligus, tanpa saya minta lagi: (1) .zip yang berisi berkas .html hasil; (2) salinan berekstensi .txt yang isinya IDENTIK karakter demi karakter dengan .html (nama sama). Jangan ubah isi saat menyalin/mengemas. Tulis ukuran kedua berkas (KB) di akhir.
```

Verifikasi Claude: jsdom dengan data uji; Rekap Mandor tanpa Ritase; 0 selisih bila semua sama.

---

## P4 — "Perlu konfirmasi" (zona): Setuju tidak boleh menambah baris rencana ganda (WAJIB)
Berkas masukan: v5d → keluaran: v5e

```
Semua balasan kepada saya dalam bahasa Indonesia.
Waktu sekarang (WIB): Jumat, 6 November 2026, [ISI JAM]

Tugas: perbaikan TERARAH pada PantauUsaha_Papan_v5d.html → simpan sebagai PantauUsaha_Papan_v5e.html. JANGAN tulis ulang. JANGAN jalankan pengujian.

Masalah: pada kartu konfirmasi Pengawas (kartuKonfirmasi, setujuiTambahRencana, tolakTambahRencana sekitar baris 2667-2762), tombol Setuju selalu menambah baris rencana BARU walau sudah ada rencana yang sama (contoh: Pemangkasan Slamet tanggal sama), sehingga rencana jadi ganda.

Ubah kartu konfirmasi menjadi tiga pilihan jelas:
A. "Petakan ke rencana yang sudah ada" — dropdown berisi baris rencana tanggal yang sama untuk pelapor yang sama yang BELUM punya laporan (tampilkan No. rencana, kegiatan, area/zona). Bila dipilih: set l.rencanaId ke rencana itu, l.diluarRencana=false, status MENUNGGU TINJAUAN; JANGAN menambah baris rencana.
B. "Tambahkan sebagai rencana baru" — perilaku lama (push baris rencana baru), hanya bila Pengawas memilih ini secara eksplisit.
C. "Tolak / kembalikan" — perilaku lama (alasan wajib → DIKEMBALIKAN KE AGEN).
Dropdown A default kosong; bila tidak ada rencana yang cocok, pilihan A nonaktif dengan teks "Tidak ada rencana kosong yang cocok".
Setiap pilihan dicatat di Audit Log dengan nama pilihan (Petakan / Tambah baru / Tolak) dan ID rencana terkait.

Jangan ubah hal lain. Tulis daftar fungsi yang diubah di akhir.

Berkas hasil WAJIB langsung disediakan sebagai DUA berkas unduhan sekaligus, tanpa saya minta lagi: (1) .zip yang berisi berkas .html hasil; (2) salinan berekstensi .txt yang isinya IDENTIK karakter demi karakter dengan .html (nama sama). Jangan ubah isi saat menyalin/mengemas. Tulis ukuran kedua berkas (KB) di akhir.
```

Verifikasi Claude: skenario Slamet Pemangkasan → Petakan → jumlah baris S.rencana tidak bertambah. Ini juga bahan demo "uji gagal lalu diperbaiki".

---

## P5 — "Belum dilaporkan": penanda SUDAH ADA LAPORAN + Report
Berkas masukan: v5e → keluaran: v5f

```
Semua balasan kepada saya dalam bahasa Indonesia.
Waktu sekarang (WIB): Jumat, 6 November 2026, [ISI JAM]

Berkas terlampir PantauUsaha_Papan_v5e.txt adalah isi PantauUsaha_Papan_v5e.html (ekstensi saja yang berbeda). Pakai berkas terlampir ini sebagai dasar; jangan memakai versi lain atau isi percakapan sebelumnya sebagai sumber isi.

Tugas: perbaikan TERARAH pada PantauUsaha_Papan_v5e.html → simpan sebagai PantauUsaha_Papan_v5f.html. JANGAN tulis ulang. JANGAN jalankan pengujian.

Masalah: agen menandai rencana yang sebenarnya sudah dilaporkan sebagai "Belum dilaporkan" karena paket hanya memberi penanda untuk rencana yang BELUM punya laporan.

1. Pada blokRencanaHariIni (sekitar baris 1921-1937): untuk SETIAP baris rencana tulis penanda eksplisit.
   - Ada laporan: "SUDAH ADA LAPORAN (ID laporan <id>, Tanda: <tanda>)"; bila lebih dari satu laporan sebut semua ID.
   - Tidak ada laporan: "BELUM DILAPORKAN (ID laporan -, Tanda: Belum dilaporkan)" (seperti sekarang).
2. Di paket Report (Matriks dan Rekap), tambahkan bagian "--- RENCANA BELUM DILAPORKAN PERIODE INI (n) ---" berisi baris rencana tanpa laporan: tanggal, pelapor, area/zona, kegiatan, No. rencana, ID rencana. Hitung dari S.rencana pada periode yang tidak punya laporan sama sekali (hitungAngkaAcuan sudah punya data rencana per tanggal; tambahkan daftar rinci).
3. Di pratinjau Report tampilkan bagian yang sama "Belum dilaporkan (n)" dan kolom "Belum final" Matriks tetap seperti sekarang.

Jangan ubah hal lain selain butir 1-3. Tulis daftar fungsi/baris yang diubah.

Berkas hasil WAJIB langsung disediakan sebagai DUA berkas unduhan sekaligus, tanpa saya minta lagi: (1) .zip yang berisi berkas .html hasil; (2) salinan berekstensi .txt yang isinya IDENTIK karakter demi karakter dengan .html (nama sama). Jangan ubah isi saat menyalin/mengemas. Tulis ukuran kedua berkas (KB) di akhir.
```

Verifikasi Claude: paket Rencana Saya (Slamet) memuat SUDAH ADA LAPORAN; paket Report memuat daftar Belum dilaporkan; ulang uji agen (kasus Anti Hama).

---

## P6 — Audit Log: jejak Report + cegah catatan ganda
Berkas masukan: v5f → keluaran: v5g

```
Semua balasan kepada saya dalam bahasa Indonesia.
Waktu sekarang (WIB): Jumat, 6 November 2026, [ISI JAM]

Tugas: perbaikan TERARAH pada PantauUsaha_Papan_v5f.html → simpan sebagai PantauUsaha_Papan_v5g.html. JANGAN tulis ulang. JANGAN jalankan pengujian.

1. Tambahkan catat() pada: (a) tombol "Baca hasil dari teks" di Report, isi: jenis report, periode, jumlah baris REKAP/MATRIKS yang terbaca, hasil Berhasil/Gagal; (b) unduhExcelReport (sekitar baris 3695) saat BERHASIL: nama berkas, jenis, periode, pelaku. Saat ini hanya penolakan yang tercatat.
2. Pada setujuiJawabanReport (sekitar baris 3417-3431): cegah klik ganda — bila persetujuan dengan kunci yang sama sudah aktif, tampilkan toast "Sudah disetujui" dan JANGAN mencatat baris Audit Log kedua.
3. Catatan Audit Log tidak boleh memuat PIN atau data sensitif.
4. Ganti semua teks "AGENTS_v9" / "AGENTS_v9.md" di aplikasi (paket header, "Lampiran", banner, paket Report) menjadi "AGENTS_v9_1" / "AGENTS_v9_1.md". Jangan ubah hal lain.

Jangan ubah hal lain. Tulis daftar baris yang diubah.

Berkas hasil WAJIB langsung disediakan sebagai DUA berkas unduhan sekaligus, tanpa saya minta lagi: (1) .zip yang berisi berkas .html hasil; (2) salinan berekstensi .txt yang isinya IDENTIK karakter demi karakter dengan .html (nama sama). Jangan ubah isi saat menyalin/mengemas. Tulis ukuran kedua berkas (KB) di akhir.
```

Verifikasi Claude: jalankan alur Report di Playwright; hitung baris Audit Log.

---

## P7 — Rencana & tampilan (UAT #9, #11, #12 + catatan Pengawas)
Berkas masukan: v5g → keluaran: v5h
Asumsi yang saya ambil (kabari Claude bila salah): zona wajib untuk area bergona (blokir saat Pengawas menyimpan rencana); tab "Minggu depan" ditambah di Rencana Saya; rentang tanggal untuk Pengawas = dua kolom Dari–Sampai.

```
Semua balasan kepada saya dalam bahasa Indonesia.
Waktu sekarang (WIB): Jumat, 6 November 2026, [ISI JAM]

Tugas: perbaikan TERARAH pada PantauUsaha_Papan_v5g.html → simpan sebagai PantauUsaha_Papan_v5h.html. JANGAN tulis ulang. JANGAN jalankan pengujian.

1. Rencana Mingguan (Pengawas): tambahkan pilihan "Dari tanggal" dan "Sampai tanggal" (rentang). Saat Simpan semua, baris yang sama dibuat untuk setiap tanggal dalam rentang (maksimal 7 hari). Aturan kuota per orang per hari tetap berlaku dan diperiksa untuk SETIAP tanggal; bila ada yang gagal, tidak ada yang tersimpan (sama seperti sekarang).
2. Rencana Saya: tambahkan tab "Minggu depan" (Sabtu–Jumat berikutnya) di samping "Hari ini" dan "Minggu ini" (fungsi rentangRencanaSaya sekitar baris 960-971, tombol sekitar baris 1122).
3. Edit rencana Driver: izinkan mengubah Area (saat ini terkunci) selama baris belum punya laporan.
4. Tombol "Setuju massal" di Rencana vs Realisasi: pindahkan/duplikasi ke dekat daftar baris yang dicentang (bar tetap/sticky di atas daftar), bukan hanya di kartu paling atas.
5. Zona WAJIB di form Rencana Mingguan (dan edit rencana) bila Area yang dipilih punya zona di master data: ganti label "(opsional)" menjadi "(wajib bila area punya zona)"; Simpan DITOLAK dengan pesan jelas per baris bila zona kosong (tidak ada yang tersimpan, seperti aturan semua-atau-tidak yang sudah ada). Area tanpa zona: zona tetap kosong/opsional. Untuk pekerjaan di dua zona, Pengawas membuat DUA baris rencana (Zona A dan Zona B); Mandor melapor masing-masing. Dengan ini rencana tanpa zona tidak muncul lagi sehingga laporan Mandor tidak jatuh menjadi "Di luar rencana" (UAT #18).

Jangan ubah hal lain. Tulis daftar fungsi/baris yang diubah.

Berkas hasil WAJIB langsung disediakan sebagai DUA berkas unduhan sekaligus, tanpa saya minta lagi: (1) .zip yang berisi berkas .html hasil; (2) salinan berekstensi .txt yang isinya IDENTIK karakter demi karakter dengan .html (nama sama). Jangan ubah isi saat menyalin/mengemas. Tulis ukuran kedua berkas (KB) di akhir.
```

Verifikasi Claude: Playwright per peran (Pengawas, Driver Samsul, Mandor); uji rentang 3 hari + kuota gagal.

---

## P8 — AGENTS v9.1 (jalur agen; kerjakan di WorkBuddy terpisah)
Berkas masukan: v9_final/AGENTS_v9.md → keluaran: AGENTS_v9_1.md (EDIT TERARAH, jangan tulis ulang)

```
Semua balasan kepada saya dalam bahasa Indonesia.
Waktu sekarang (WIB): Jumat, 6 November 2026, [ISI JAM]

Berkas terlampir AGENTS_v9.md adalah dasar; jangan memakai versi lain atau isi percakapan sebelumnya sebagai sumber isi.

Tugas: edit TERARAH pada AGENTS_v9.md → simpan sebagai AGENTS_v9_1.md. JANGAN tulis ulang. Hanya tambah/ubah butir berikut; sisanya tetap.

1. Butir 18 (Belum dilaporkan): sebuah rencana dinyatakan "Belum dilaporkan" HANYA bila paket memuat penanda "BELUM DILAPORKAN". Bila penanda "SUDAH ADA LAPORAN (ID ...)" ada, JANGAN menyebut Belum dilaporkan. Bila penanda tidak ada sama sekali untuk sebuah rencana, tulis "tidak dapat diverifikasi dari paket ini" — jangan menebak.
2. Butir 19 (Report): jangan membuat baris SELISIH bila hasil sama dengan angka acuan atau bila item "tidak berlaku" (mis. ritase Mandor). Cukup satu baris "SELISIH | semua item | - | - | tidak ada selisih".
3. Butir 19: CATATAN KLIEN wajib menyebut daftar rencana "Belum dilaporkan" dari bagian "RENCANA BELUM DILAPORKAN" bila ada, dan laporan tanda DI LUAR RENCANA/Perlu konfirmasi, tanpa gaji.
4. Jangan bergantung pada ingatan chat sebelumnya: hanya gunakan data di paket yang ditempel pada pesan ini. Bila paket tidak memuat sesuatu, tulis "tidak ada di paket".
5. Format jawaban: tulis satu baris per item persis format paket. JANGAN memakai karakter bullet ("-", "*", angka) di awal baris dan JANGAN membungkus jawaban dengan tanda ``` (aplikasi menandai baris asing sebagai merah).

Di akhir tulis daftar butir yang diubah.

Berkas hasil WAJIB langsung disediakan sebagai DUA berkas unduhan sekaligus: (1) .zip berisi berkas hasil; (2) salinan .txt yang isinya IDENTIK. Jangan ubah isi saat menyalin/mengemas.
```

Verifikasi Claude: diff terhadap v9; ulangi uji agen (4 laporan + Rekap + Matriks); salin ke repo.

---

## Catatan keputusan & ROADMAP (tidak dikerjakan Jumat)
- **#18 Zona**: akar masalah (rencana tanpa zona) ditutup oleh P7 butir 5 (zona wajib bagi Pengawas). Alur 'satu laporan untuk dua zona' di sisi Mandor TIDAK dibuat; cukup dua baris rencana = dua laporan.
- **#20 Driver multi-ritase per area**: BERTENTANGAN dengan keputusan 3 Nov 20.47 (satu laporan = satu ritase). Tidak diubah; masuk roadmap, perlu keputusan Rany bila ingin dibuka lagi.
- **Foto**: aplikasi hanya menyimpan nama berkas; agen memeriksa nama saja. Struktur penyimpanan usulan ada di catatan-perubahan-tertunda.md → roadmap, diungkap jujur di dokumen.
- UAT yang masih LEWATI (#22, 24–26, 34, 37–39): uji ulang setelah P1–P7 bila waktu ada.

## Setelah semua prompt
Claude: diff tiap versi, uji Playwright, jalankan ulang Rekap (kasus uji basi) dan alur Perlu konfirmasi (demo "gagal lalu diperbaiki"), simpan sha256 versi akhir, salin ke repo sebagai PantauUsaha_Papan_v6.html.

---

## P9 (OPSIONAL, hanya bila uji P9-0 lulus) — Simpan foto + agen meninjau foto
### P9-0 — Uji dulu: apakah agen WorkBuddy bisa membaca gambar? (tanpa ubah aplikasi)
Kerjakan SEBELUM membangun apa pun. Chat baru di WorkBuddy, lampirkan 2 foto mock (mis. foto taman/jalan yang Rany ambil sendiri, tanpa orang dan tanpa data pribadi), lalu kirim:
```
Semua balasan kepada saya dalam bahasa Indonesia.
Waktu sekarang (WIB): Jumat, 6 November 2026, [ISI JAM]

Saya melampirkan 2 foto. Untuk tiap foto jawab singkat: (1) apakah kamu benar-benar dapat MELIHAT isi gambar, atau hanya membaca nama berkasnya? (2) sebutkan apa yang tampak (benda, kondisi, perkiraan area kerja). (3) Jika kamu tidak bisa melihat gambar, katakan terus terang "tidak bisa melihat". Jangan menebak dari nama berkas.
```
Hasil: lulus = agen menyebut isi yang benar dan bisa dicek Rany; gagal = agen menebak dari nama berkas / menolak. Catat model (Auto) dan saldo.

### P9 — rancangan bila lulus (draf; Claude perbaiki setelah hasil P9-0)
- Aplikasi: saat unggah foto laporan, perkecil di browser (sisi terpanjang 800 px, JPEG ~0,6) dan simpan sebagai data URL di penyimpanan lokal (batas ±5 MB total → maks ±3 foto per laporan; tampilkan peringatan bila penuh); tampilkan miniatur di Rencana vs Realisasi untuk Pengawas.
- Paket agen: foto TIDAK ikut teks tempel; tombol "Unduh foto laporan ini" menghasilkan berkas gambar bernama sesuai ID laporan, yang Rany lampirkan manual di WorkBuddy bersama paket teks. AGENTS: "periksa kesesuaian isi foto dengan kegiatan; bila tidak dapat dilihat, tulis tidak dapat diverifikasi".
- Keterbatasan jujur: tanpa server, foto hanya ada di peramban satu perangkat; penyimpanan sungguhan (cloud storage) = roadmap.

---

## P10 (OPSIONAL, perubahan rancangan Driver — UAT #20) — dikerjakan setelah P1–P8 lulus verifikasi
Koreksi dari catatan sebelumnya: aturan "1 LAPORAN = 1 RITASE" tetap benar dan TIDAK diubah. Yang berbeda dengan rancangan Rany adalah sisi RENCANA: aplikasi sekarang membuat "1 BARIS RENCANA = 1 RITASE", sehingga Driver hanya bisa melapor sebanyak baris yang dibuat Pengawas. Rancangan Rany: Pengawas menugaskan Driver ke Area + kegiatan (tanpa menentukan jumlah ritase); Driver melapor berkali-kali; batas hanya total ritase per hari lintas semua Area (1–4 normal, 5–7 lembur, >7 konfirmasi Pengawas).

### P10a — Laporan Driver
Berkas masukan: versi terakhir yang lulus → keluaran: versi berikutnya
```
Semua balasan kepada saya dalam bahasa Indonesia.
Waktu sekarang (WIB): Jumat, 6 November 2026, [ISI JAM]

Tugas: perubahan TERARAH khusus peran Driver pada berkas [NAMA VERSI TERAKHIR].html → simpan sebagai versi baru (nama berikutnya). JANGAN tulis ulang. JANGAN jalankan pengujian. Peran Mandor tidak boleh berubah perilakunya.

Aturan baru Driver:
1. Rencana Driver = penugasan (tanggal + Area + kegiatan). Satu baris rencana Driver BOLEH dilaporkan berkali-kali; baris tetap tampil di "Rencana hari ini" Driver setelah dilaporkan, dengan keterangan "sudah n ritase".
2. Setiap laporan Driver = 1 ritase. Nomor ritase terisi OTOMATIS = jumlah laporan Driver itu pada tanggal tersebut (lintas semua Area, kecuali yang DIKEMBALIKAN/dibatalkan) + 1. Driver tidak mengetik nomor ritase.
3. Batas per Driver per hari, lintas semua Area: ritase 1–4 normal; 5–7 ditandai LEMBUR (seperti aturan lembur yang sudah ada); ritase ke-8 dan seterusnya DITOLAK dengan pesan "Lebih dari 7 ritase: ajukan ke Pengawas" dan dicatat di Audit Log.
4. Pada form Rencana Mingguan, untuk Driver: satu baris = satu penugasan (tanpa menghitung ritase); hapus pemeriksaan "maksimal 7 baris" untuk Driver (batas 7 dipindah ke pelaporan di atas). Aturan Mandor (maks 5 kegiatan) tetap.
5. Di Rencana vs Realisasi: baris penugasan Driver menampilkan semua laporan ritasenya; status Setuju/Tidak setuju tetap per LAPORAN.

Tulis di akhir daftar fungsi/baris yang diubah dan bagian yang BELUM disesuaikan (mis. Report, Belum dilaporkan) tanpa mengubahnya.

Berkas hasil WAJIB langsung disediakan sebagai DUA berkas unduhan sekaligus, tanpa saya minta lagi: (1) .zip yang berisi berkas .html hasil; (2) salinan berekstensi .txt yang isinya IDENTIK karakter demi karakter dengan .html (nama sama). Jangan ubah isi saat menyalin/mengemas. Tulis ukuran kedua berkas (KB) di akhir.
```
### P10b — Menyesuaikan Report & Belum dilaporkan untuk Driver (prompt terpisah setelah P10a diverifikasi)
Poin: baris rencana Driver dianggap "Belum dilaporkan" bila 0 laporan; kolom "rencana" Matriks untuk Driver = jumlah penugasan; Ritase di Rekap = jumlah laporan CLOSED Driver (sudah demikian); paket agen memuat "SUDAH ADA LAPORAN (ID a, b, c)" untuk semua ID. Claude menulis prompt rincinya setelah melihat hasil P10a.

Risiko (perkiraan): menyentuh pembuatan laporan, kuota, Rencana vs Realisasi → cakupan lebih besar dari P1–P7; kerjakan hanya bila P1–P8 sudah lulus dan masih ada waktu rekaman demo. Bila tidak sempat: tulis sebagai keterbatasan rancangan dan jelaskan di demo bahwa workaround-nya Pengawas membuat satu baris per ritase.
