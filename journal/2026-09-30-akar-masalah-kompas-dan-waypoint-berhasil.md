# 2026-09-30: Akar masalah kompas ditemukan, misi waypoint berhasil

## Yang dikerjakan
- Troubleshooting kompas seharian: kalibrasi berulang kali gagal atau berkualitas merah, `Check mag field (xy diff)` terus melewati ambang dengan nilai naik-turun (104 → 282), selisih heading ~23 derajat terhadap kompas HP.
- `COMPASS_USE2` dan `COMPASS_USE3` dinonaktifkan; hanya kompas eksternal yang dipakai.
- Lokasi terbang dipindah 300–400 m menjauh dari menara telekomunikasi → **semua gejala kompas hilang**. Lihat [failures/004](../failures/004-crash-misi-auto-gangguan-kompas.md).
- **Misi waypoint berhasil dijalankan.**
- `RTL_ALT` diturunkan ke 5 m untuk latihan di lapangan terbuka.

## Yang dipelajari
- Gangguan kompas bisa berasal dari lingkungan, bukan hanya dari tata letak drone. Ciri khasnya: nilai mag field berubah-ubah drastis tanpa ada perubahan apa pun di drone (gangguan internal cenderung konstan).
- ROI membuat hidung drone terkunci ke satu titik; tidak dipakai untuk mapping, cukup `WP_YAW_BEHAVIOR` = face next waypoint.
- RTL hover di atas home selama `RTL_LOIT_TIME` lalu turun; drone berhenti menggantung kalau `RTL_ALT_FINAL` > 0.
- `RTL_ALT` rendah hanya aman di lapangan tanpa halangan.

## Catatan
- Log `.bin` penerbangan sukses ini **tidak sempat diunduh**. `.param` sudah disimpan.

## Next step
- Kalibrasi ulang kompas di lokasi bersih, targetkan indikator hijau (kalibrasi terakhir yang tersimpan dibuat di dekat menara).
- Unduh log `.bin` setiap selesai terbang.
