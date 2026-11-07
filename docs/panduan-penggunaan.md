# Panduan Penggunaan / User Guide

All data is mock data. The app is one HTML file; data is kept in your own browser (localStorage), so a fresh visit starts empty. Semua data adalah data tiruan; data tersimpan di peramban masing-masing, sehingga kunjungan pertama selalu kosong.

App / Aplikasi: https://ranyrpw-creator.github.io/pantauusaha-ai/

## Quick start (English)
1. **Open the app.** The red banner says "DATA TIRUAN" (mock data). Choose a role from the dropdown.
2. **Load sample data.** Choose **Hadi (Pengawas)**, enter PIN `1234`, click **Masuk**. Open **Master Data**, scroll to **Cadangan data**, click **Muat data contoh**, confirm with OK. The app now holds master data and several plan items dated today.
3. **File a field report.** Click **Ganti**, choose **Slamet (Mandor) — Area Selatan** (no PIN). Open **Lapor**, pick an activity from today's plan (or "Di luar rencana", which requires Area and Zona), attach 1-2 photos (any image) and a note of at least 2 characters, click **Kirim laporan**. The report gets status BARU.
4. **Send to the agent.** Log in again as Hadi (PIN `1234`). Open **Agen**, click **Salin perintah ke agen**. The app builds one self-contained text package. Paste it into WorkBuddy with `agent/AGENTS_v9_1.md` attached. This step needs a WorkBuddy account; the demo video shows it end to end.
5. **Bring the agent's answer back.** Copy the agent's reply (one line per report: `report ID | label | note | plan ID`), paste it into **Tempel hasil dari agen**, click **Baca hasil dari teks**, then **Simpan hasil agen**. Lines that are not valid are rejected. The report moves to a human-review status.
6. **Decide as supervisor.** Open **Rencana vs Realisasi**. Use **Setuju** (report becomes CLOSED) or **Tidak setuju** (a reason is required). For an off-plan report use **Petakan ke rencana ini**, **Tambah baru**, or **Tolak** (reason required).
7. **Check the trail.** **Audit Log** (Pengawas, Admin, Pemilik) shows who did what and when. **Riwayat** shows the history of each report.

Reset: **Atur ulang data** (bottom of the page) or **Muat data contoh** again. Backup: **Cadangkan data (.json)** in Master Data.

Without WorkBuddy you can still try steps 1-4 (up to copying the prompt) and steps 6-7 on sample data; the agent's role in steps 4-5 is shown in the demo video and in `docs/hasil-uji-T1.md` and `docs/hasil-uji-T2.md`.

## Panduan singkat (Indonesia)
1. Buka aplikasi, pilih peran. 2. Masuk sebagai **Hadi (Pengawas)**, PIN `1234`, lalu **Master Data → Cadangan data → Muat data contoh**. 3. **Ganti** ke **Slamet (Mandor)**, buka **Lapor**, isi laporan (foto 1-2 dan keterangan minimal 2 karakter), **Kirim laporan**. 4. Kembali sebagai Hadi, menu **Agen → Salin perintah ke agen**, tempel di WorkBuddy dengan `AGENTS_v9_1.md` terlampir. 5. Tempel jawaban agen di **Tempel hasil dari agen → Baca hasil dari teks → Simpan hasil agen**. 6. Di **Rencana vs Realisasi**, pilih **Setuju**, **Tidak setuju**, atau (untuk di luar rencana) **Petakan ke rencana ini / Tambah baru / Tolak**. 7. Lihat **Audit Log** untuk jejak lengkap.

## Limits / Batas
- Data is stored per browser; there is no server or database by design. Every agent step goes through a human copy-and-paste.
- The agent cannot read photo contents. Kendala and Temuan (field issue) rules exist in AGENTS.md but are not in the app yet.
