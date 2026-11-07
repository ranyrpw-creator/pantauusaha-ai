# Hasil uji agen T1

**Tujuan:** memastikan agen tidak lagi salah menyebut laporan yang sudah ada sebagai "Belum dilaporkan", dan bahwa seluruh alur (lapor → agen → tinjauan manusia → CLOSED) tercatat di Audit Log.

| Item | Isi |
|---|---|
| Tanggal | Jumat 6 November 2026, 14.41–17.46 WIB |
| Aplikasi / aturan agen | PantauUsaha_Papan_v5g / AGENTS_v9_1 |
| Agen | WorkBuddy, model Auto, chat baru (44 detik) |
| Kredit | 144 → 140 (±4,6 kredit per uji) |
| Data | Tiruan |
| Hasil | **13 dari 13 langkah LULUS** |

## Sebelum dan sesudah
- **Sebelum** (uji 5 Nov 23.30, aplikasi v5 + AGENTS v9): agen menyebut Anti Hama zona A dan Pemangkasan Slamet No. 3 dan 6 sebagai "Belum dilaporkan", padahal sudah dilaporkan. Penyebab: paket hanya memberi penanda untuk rencana yang belum dilaporkan, sehingga agen menebak sisanya.
- **Perbaikan:** paket kini menandai setiap rencana SUDAH ADA LAPORAN atau BELUM DILAPORKAN (P5); AGENTS v9.1 butir 18 melarang menyebut Belum dilaporkan tanpa penanda.
- **Sesudah** (T1): hanya Penyiangan Zona A dan Pemangkasan No. 3 yang disebut Belum dilaporkan. Kasus lama tidak berulang.

## Peran manusia dan agen
Agen hanya memberi tanda dan catatan. Pengawas membaca hasilnya, lalu menekan Setuju (laporan CLOSED). Agen tidak menulis Audit Log; aplikasi mencatat tindakan manusia. Agen juga menyatakan "isi foto tidak diketahui", jadi tidak mengaku melihat foto.

## Temuan dan keterbatasan yang jujur
1. Tombol Setuju versi lama menambah baris rencana ganda; diperbaiki lewat P4, tetapi data lama masih menyimpan sisanya.
2. Markdown di WorkBuddy mengubah "-" di awal baris menjadi bullet; aplikasi tetap membaca baris itu (3 terbaca, 0 bermasalah), dan aturan agen melarang bullet.
3. Cacat kosmetik: penanda "Tanda: <ID laporan>: -" mengulang ID; audit "Setujui report" masih memakai istilah "jumlah SELISIH". Dicatat di backlog.
4. Agen belum bisa membaca isi foto; aplikasi hanya menyimpan nama berkas. Roadmap.

Bukti: `uji-agen-T1_v3.xlsx` (langkah dan temuan) dan paket tangkapan layar T1 (15 berkas, disimpan di luar repo publik karena memuat email dan saldo).
