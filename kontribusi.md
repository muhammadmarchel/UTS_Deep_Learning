# Kontribusi Anggota

Kontribusi dinilai dari GitHub (commit dan pull request) dan dari kemampuan menjelaskan bagian yang diklaim.
Repositori kelompok: https://github.com/marcheliano-satrio/UTS_Deep_Learning

| Nama | GitHub | Peran utama | Pull request |
|---|---|---|---|
| Satrio Arjuna Putra | `SatrioArjunaPutra` | Kerangka repo dan aturan proyek; **Task 1** (klasifikasi multimodal) dan **Task 3** (clustering multimodal) utuh; integrasi `reproduce.py`, `kode/README.md`, `weights/`, ketiga file prediksi; bab Task 1 dan Task 3; review & merge PR Marchel | [#1](https://github.com/marcheliano-satrio/UTS_Deep_Learning/pull/1) kerangka, [#2](https://github.com/marcheliano-satrio/UTS_Deep_Learning/pull/2) Task 1, [#3](https://github.com/marcheliano-satrio/UTS_Deep_Learning/pull/3) Task 3, [#4](https://github.com/marcheliano-satrio/UTS_Deep_Learning/pull/4) integrasi, [#5](https://github.com/marcheliano-satrio/UTS_Deep_Learning/pull/5) README |
| M Marcheliano Taji Suryana | `muhammadmarchel` | **Task 2** (RUL): memahami dan memverifikasi kode, cek kebocoran data, bab Task 2; finalisasi laporan: pendahuluan, kesimpulan, penggabungan menjadi `laporan.pdf`, `kode/tabel_laporan.py`, `docs/tabel_laporan.md`, `kontribusi.md`, `docs/persiapan_lisan.md` | [#6](https://github.com/marcheliano-satrio/UTS_Deep_Learning/pull/6) Task 2, TODO: link PR laporan |

Catatan pembagian kerja: training semua task dijalankan di laptop Satrio (GPU RTX 3050). Kode Task 2 disusun
di laptop itu lalu diserahkan ke Marchel. Marchel membaca, memverifikasi, dan menulis bab Task 2, lalu
membukanya sebagai PR #6.

## Penggunaan alat AI

**Alat:** Claude Code (Anthropic), dijalankan di VS Code oleh kedua anggota.

**Bagian yang dibantu:**
- Menyusun kerangka repositori, aturan proyek (`CLAUDE.md`), dan urutan kerja.
- Menulis draf kode untuk ketiga task (EDA, preprocessing, model, skrip eksperimen, `reproduce.py`,
  `cek_submission.py`, `tabel_laporan.py`, `laporan/buat_pdf.py`) dan menjalankannya di laptop kelompok.
- Menyusun draf bab laporan (Task 1–3, pendahuluan, kesimpulan) dari angka di `runs/*/metrics.json`, serta
  draf `docs/persiapan_lisan.md`.
- Membantu memeriksa kode: penelusuran kebocoran data dan pencocokan angka laporan dengan file hasil run.

**Cara kelompok memverifikasi:**
- Uji unit kecil: `python kode/metrik.py` (skor asimetris dan macro-F1 dicek terhadap nilai yang dihitung
  manual) serta `python kode/task1_klasifikasi/task1_model.py` dan `python kode/task2_rul/task2_model.py`
  (bentuk keluaran tiap arsitektur).
- `cek_submission.py` diuji dengan file yang sengaja salah (kelas salah tulis, ID duplikat, kolom salah,
  cluster desimal), dan semuanya benar ditolak.
- Sanity check overfit satu batch untuk Task 1 (`runs/t1_sanity_overfit`) dan smoke test di subset kecil
  (`--smoke`).
- Pemeriksaan kebocoran data Task 2 dengan membaca kode: statistik normalisasi di-fit ulang per fold latih,
  window dan penanganan spike/NaN hanya memakai siklus ≤ t, split `GroupKFold` per `id_unit`, dan data uji
  hanya untuk prediksi akhir.
- Setiap angka di bab laporan ditelusuri ke `runs/<run>/metrics.json` atau CSV di `runs/*_tabel/`. Angka yang
  dihitung dari dua nilai (selisih, rasio, persentase) dihitung ulang, dan klaim kualitatif (mis. "resep awal
  overfit") dicek terhadap `history.json`.
- Reproduksi: `python kode/reproduce.py --data data_uts_dl --task all` (mode cepat dari `weights/`)
  menghasilkan ulang angka yang sama dengan laporan (`runs/reproduce/hasil.json`; mis. Task 2 RMSE 19,5358
  dan skor 97.209,7, sama dengan `runs/t2_cv_gru`), dan ketiga file prediksi lolos `cek_submission.py`.
- TODO Satrio: tambahkan pemeriksaan yang kamu lakukan sendiri untuk Task 1 dan Task 3.
- TODO Marchel: smoke test `python kode/task2_rul/task2_train.py --data data_uts_dl --model gru --mode cv --smoke`
  setelah data tersedia di laptop Marchel.

AI tidak dipakai untuk mengarang angka. Bila sebuah angka belum ada di file hasil run, angka itu ditulis
"belum dijalankan".

**Persetujuan** (diisi sendiri oleh tiap anggota):
- Satrio Arjuna Putra — TODO tanggal
- M Marcheliano Taji Suryana — TODO tanggal
