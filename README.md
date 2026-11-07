# PantauUsaha AI

Agen kantor untuk UMKM jasa perawatan dan kebersihan taman: membandingkan laporan lapangan dengan rencana mingguan, lalu menyerahkan keputusan akhir kepada manusia.

Tencent Cloud AI CAN DO IT Hackathon Indonesia 2026 — Track B (Agen Kantor). Tim: PantauUsaha AI (1 orang).

> **Semua data adalah data tiruan.** Nama, lokasi, plat, dan PIN adalah contoh. Tidak ada data klien sungguhan.

**Coba langsung (tanpa instalasi):** https://ranyrpw-creator.github.io/pantauusaha-ai/

## Isi repo
| Folder | Isi |
|---|---|
| `index.html` | PantauUsaha Papan v5g, salinan aplikasi untuk GitHub Pages (sama dengan `app/PantauUsaha_Papan_v5g.html`). |
| `app/` | PantauUsaha Papan (`PantauUsaha_Papan_v5g.html`): satu berkas HTML, buka di browser. Data tersimpan di browser (localStorage). |
| `agent/` | `AGENTS_v9_1.md`: aturan agen untuk WorkBuddy (format jawaban, penanda Belum dilaporkan, larangan menulis audit log). |
| `prompts/` | Perintah yang dipakai untuk membangun/memperbaiki aplikasi di WorkBuddy. |
| `tests/` | Hasil uji: UAT aplikasi, uji agen T1 dan T2 (kasus, hasil, status), skenario demo. |
| `docs/` | Ringkasan hasil uji T1 dan T2, catatan temuan dan perubahan tertunda. |
| `data-contoh/` | Profil usaha, rencana, dan laporan contoh (tiruan). |

## Cara kerja singkat
1. Mandor mengisi laporan lapangan di aplikasi; Pengawas menyusun rencana mingguan.
2. Menu **Agen** membuat perintah; Pengawas menyalinnya ke agen (WorkBuddy).
3. Hasil agen ditempel kembali ke aplikasi, dibaca sebagai baris `ID laporan | Tanda | catatan | ID rencana`.
4. Di **Rencana vs Realisasi**, Pengawas menyetujui atau menolak (alasan wajib). Agen tidak pernah memutuskan sendiri.
5. Semua tindakan manusia/aplikasi tercatat di **Audit Log**; agen tidak menulis audit log.

Peran: Pengawas, Mandor, Driver, Admin, dengan izin menu berbeda. Lima Tanda dari agen: Sesuai, Tidak sesuai, Di luar rencana, Perlu konfirmasi, Belum dilaporkan.

## Cakupan
**Sudah ada:** rencana mingguan, laporan lapangan per peran, jembatan salin-tempel ke agen, pembaca hasil agen dengan validasi, persetujuan manusia, Audit Log, ekspor/rekap, cadangan data.

**Aturannya ada di AGENTS.md, belum ada di aplikasi:** pencatatan Kendala dan Temuan (masalah lapangan) beserta rantai persetujuannya.

**Rencana pengembangan:** pembacaan foto laporan, Driver multi-ritase, penyempurnaan tampilan.

## Hasil uji (data tiruan)
- **T1:** 13 dari 13 langkah lulus; kasus "agen salah menyebut Belum dilaporkan" tidak berulang setelah paket menandai setiap rencana (`docs/hasil-uji-T1.md`).
- **T2:** 10 dari 10 langkah lulus; laporan di luar rencana ditandai Perlu konfirmasi, dipetakan Pengawas, dan tercatat di Audit Log (`docs/hasil-uji-T2.md`).
- **Temuan jujur:** paket yang sama dijalankan dua kali menghasilkan jawaban berbeda (Sesuai lalu Perlu konfirmasi). Karena itu keputusan akhir selalu di tangan manusia.

## Cara mencoba
Buka tautan Pages di atas, atau `index.html` / `app/PantauUsaha_Papan_v5g.html` di Chrome. Masuk sebagai Pengawas (PIN contoh `1234`). Menu Master Data → Cadangan data → "Muat data contoh" mengisi data tiruan. Untuk bagian agen, pakai WorkBuddy dengan `agent/AGENTS_v9_1.md` terlampir.

## Keterbatasan yang diketahui
- Agen tidak membaca isi foto; foto laporan belum didukung penuh (rencana pengembangan).
- Hasil agen bisa berbeda antarjalan untuk paket yang sama; manusia selalu meninjau.
- Beberapa temuan kecil masih terbuka; lihat `docs/catatan-perubahan-tertunda.md`.
- Beberapa kasus UAT berstatus GAGAL/LEWATI; lihat `tests/UAT-aplikasi-v5_v2.xlsx`.
- Data tersimpan per browser (localStorage), bukan di server.

## Pengungkapan (disclosure)
Aplikasi dan agen dibangun dengan WorkBuddy. Claude (Anthropic) membantu menulis perintah, memeriksa hasil, dan menyusun dokumen uji serta materi pengiriman; hasil WorkBuddy diverifikasi ulang di luar WorkBuddy. Dataset dibuat sendiri.
