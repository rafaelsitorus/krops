# 2026-09-29: Penghalusan kendali, lalu crash di misi AUTO

## Yang dikerjakan
- Kendali joystick terasa terlalu sensitif (yaw dan pitch menyentak), lalu diperhalus:
  - `ATC_ANGLE_MAX` 30 → 10 derajat (satuan derajat di 4.7, bukan centi-derajat)
  - `PILOT_Y_RATE` 202,5 → 60 °/s, `PILOT_Y_EXPO` Medium, `PILOT_Y_RATE_TC` 0,3
  - `ATC_INPUT_TC` 0,5; `PILOT_SPD_UP` / `PILOT_SPD_DN` 50
- Parameter misi (nama `WP_` dan satuan m/s di 4.7): `WP_SPD` 3, `WP_ACC` 1, `WP_SPD_UP` 1, `WP_SPD_DN` 0,75, `WP_RFND_USE` disable.
- Misi AUTO dijalankan → **crash**. Lihat [failures/004](../failures/004-crash-misi-auto-gangguan-kompas.md).

## Yang dipelajari
- `ATC_ANGLE_MAX` berlaku di semua mode termasuk AUTO, jadi nilai rendah untuk latihan manual harus dikembalikan (25–30) sebelum misi. Parameter `PILOT_*` dan `ATC_INPUT_TC` hanya memengaruhi kendali manual.
- Untuk membatasi kecepatan misi, pakai `WP_SPD`, bukan `ATC_ANGLE_MAX`.
