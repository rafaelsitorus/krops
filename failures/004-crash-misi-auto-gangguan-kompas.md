# 004: Crash di misi AUTO — gangguan kompas dari menara telekomunikasi

**Tanggal:** 2026-09-29 (crash), akar masalah ditemukan 2026-09-30

## Apa yang terjadi
Misi AUTO pertama berakhir crash 26 detik setelah takeoff. Urutan dari log:

| Waktu | Pesan |
|---|---|
| +2 s | `MAG1 ground mag anomaly, yaw re-aligned` |
| +6 s | `EKF3 IMU0 emergency yaw reset` |
| +9 s | `GPS Glitch or Compass error` |
| +10 s | `EKF Failsafe, EKF variance` |
| +13–17 s | `Circle fence breached` ×5, `Mode change to RTL failed: requires position` ×5 |
| +24 s | `Crash: Disarming: AngErr=36>30` |

Failsafe tidak bisa menyelamatkan: RTL butuh estimasi posisi, dan posisi sudah runtuh bersama kompas.

## Akar masalah
Gangguan elektromagnetik dari **menara telekomunikasi dalam radius 100–150 m** dari lokasi terbang. Dipastikan pada 2026-09-30: setelah lokasi dipindah 300–400 m menjauh, semua gejala hilang dan misi waypoint berhasil.

## Gejala yang seharusnya dibaca lebih awal
- Kalibrasi kompas macet di ~60%, atau selesai dengan indikator **merah**.
- `Check mag field (xy diff)` melewati ambang 100 dengan nilai **berubah-ubah** (104 → 282). Gangguan internal cenderung konstan; nilai yang melompat-lompat menunjuk ke sumber eksternal.
- Selisih heading ~23 derajat terhadap kompas HP.
- `ground mag anomaly` berulang sejak beberapa sesi sebelumnya, termasuk saat masih di darat.

## Pelajaran
- **Tambahkan survei lokasi ke pre-flight checklist**: menara telko, SUTET, dan struktur logam besar. Jarak aman terukur: >300 m.
- Kalibrasi kompas hanya valid kalau dilakukan di lokasi yang bersih. Hasil kalibrasi merah tidak boleh dipakai terbang.
- Peringatan kompas berulang adalah **blocker mutlak** untuk misi AUTO, bukan sekadar catatan. Di AUTO tidak ada pilot yang bisa mengoreksi arah, dan kehilangan heading berujung kehilangan posisi.
- Diagnosis sempat terlalu lama terpaku pada tata letak kompas di dalam drone, padahal mast sudah terpasang.
