# Hasil uji agen T2

**Tujuan:** menguji laporan di luar rencana. Mandor Slamet melapor Penyiangan Zona A yang tidak dipilih dari rencana; agen menandai, Pengawas memutuskan (Petakan ke rencana yang sudah ada), lalu seluruh rantai tercatat di Audit Log.

| Item | Isi |
|---|---|
| Tanggal | Jumat 6 November 2026, 20.21–21.12 WIB |
| Aplikasi / aturan agen | PantauUsaha_Papan_v5g / AGENTS_v9_1 |
| Agen | WorkBuddy, model Auto, chat baru (1 menit 14 detik, ±6,15 kredit) |
| Data | Tiruan |
| Hasil | **10 dari 10 langkah LULUS** |

## Yang terbukti
- Aplikasi menolak laporan di luar rencana tanpa Zona dan tanpa keterangan; penolakan tercatat di Audit Log.
- Agen menandai **Perlu konfirmasi** (bukan Sesuai, bukan Di luar rencana) karena penanda paket (rencana No. 4 BELUM DILAPORKAN) bertentangan dengan data laporan yang cocok penuh. Keputusan diserahkan ke Pengawas.
- Petakan ke rencana tidak menambah baris rencana; daftar Belum dilaporkan turun dari 2 menjadi 1 setelah Setuju (perbaikan P4 terbukti).
- Rantai Audit Log lengkap: ditolak, kirim laporan, kirim ke agen, baca hasil, catat hasil agen, petakan, setujui. Agen tidak menulis Audit Log.

## Temuan dan keterbatasan yang jujur
1. Rencana awal "zona kosong → Perlu konfirmasi" tidak bisa dipicu lewat aplikasi karena aplikasi sudah menolak zona kosong; skenario diubah. Aturan itu tetap sebagai jaring pengaman.
2. Paket dan banner menu Agen masih menyebut "file Excel bila ada kegiatan di luar rencana" (sisa mode berkas); agen mencatatnya sebagai celah.
3. Penanda "Tanda: <ID laporan>: -" dibaca agen sebagai Tanda kosong, sehingga 6 rencana lain ditulis "tidak dapat diverifikasi" (cacat berdampak kecil).
4. Jawaban agen panjang (proses berpikir ikut tertulis).
5. Agen menulis rencana No. 4 dua kali (Perlu konfirmasi dan Belum dilaporkan); hasil akhir benar setelah Petakan, tetapi perlu dipantau agar tidak terhitung ganda.
6. Kosmetik: baris dipetakan tampil "ke-4", dropdown menampilkan ID internal, Tanda agen tetap "Perlu konfirmasi" setelah CLOSED.

## Satu pengujian ulang saat merekam demo
Paket yang sama dijalankan dua kali (6 November, malam). Jalan 1: agen menjawab **Sesuai**, menyimpang dari aturan butir 18b. Jalan 2: **Perlu konfirmasi**, sesuai aturan. Agen tidak sepenuhnya konsisten antarjalan, sehingga keputusan akhir tetap di tangan manusia. Temuan dan dua usulan aturan baru ada di `catatan-perubahan-tertunda.md`.

Bukti: `tests/uji-agen-T2_v4.xlsx` (langkah dan temuan). Tangkapan layar uji disimpan di luar repo publik karena memuat email dan saldo.
