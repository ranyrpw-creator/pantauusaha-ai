# PantauUsaha AI

Agen kantor untuk UMKM jasa perawatan dan kebersihan taman: membandingkan laporan lapangan dengan rencana mingguan, lalu menyerahkan keputusan akhir kepada manusia.

Tencent Cloud AI CAN DO IT Hackathon Indonesia 2026 — Track B (Agen Kantor). Tim: PantauUsaha AI (1 orang).

> **Semua data adalah data tiruan.** Nama, lokasi, plat, dan PIN adalah contoh. Tidak ada data klien sungguhan.

## Isi repo
| Folder | Isi |
|---|---|
| `app/` | PantauUsaha Papan (`PantauUsaha_Papan_v5g.html`): satu berkas HTML, buka di browser. Data tersimpan di browser (localStorage). |
| `agent/` | `AGENTS_v9_1.md`: aturan agen untuk WorkBuddy (format jawaban, penanda Belum dilaporkan, larangan menulis audit log). |
| `prompts/` | Perintah yang dipakai untuk membangun/memperbaiki aplikasi di WorkBuddy. |
| `tests/` | Hasil uji: UAT aplikasi, uji agen T1 (kasus, hasil, status), skenario demo. |
| `docs/` | Catatan temuan dan perubahan tertunda. |
| `data-contoh/` | Profil usaha, rencana, dan laporan contoh (tiruan). |

## Cara kerja singkat
1. Mandor mengisi laporan lapangan di aplikasi; Pengawas menyusun rencana mingguan.
2. Menu **Agen** membuat perintah; Pengawas menyalinnya ke agen (WorkBuddy).
3. Hasil agen ditempel kembali ke aplikasi, dibaca sebagai baris `ID laporan | Tanda | catatan | ID rencana`.
4. Di **Rencana vs Realisasi**, Pengawas menyetujui atau menolak (alasan wajib). Agen tidak pernah memutuskan sendiri.
5. Semua tindakan manusia/aplikasi tercatat di **Audit Log**; agen tidak menulis audit log.

Peran: Pengawas, Mandor, Driver, Admin, dengan izin menu berbeda.

## Cara mencoba
Buka `app/PantauUsaha_Papan_v5g.html` di Chrome. Masuk sebagai Pengawas (PIN contoh `1234`). Untuk bagian agen, pakai WorkBuddy dengan `agent/AGENTS_v9_1.md` terlampir.

## Keterbatasan yang diketahui
- Foto laporan belum didukung (rencana pengembangan).
- Beberapa temuan kecil masih terbuka; lihat `docs/catatan-perubahan-tertunda.md`.
- Beberapa kasus UAT berstatus GAGAL/LEWATI; lihat `tests/UAT-aplikasi-v5_v2.xlsx`.

## Pengungkapan (disclosure)
Aplikasi dan agen dibangun dengan WorkBuddy. Claude (Anthropic) membantu menulis perintah, memeriksa hasil, dan menyusun dokumen uji; hasil WorkBuddy diverifikasi ulang di luar WorkBuddy. Dataset dibuat sendiri.
