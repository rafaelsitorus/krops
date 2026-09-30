# 2026-09-22: Flashing ArduCopter dan motor test

## Tujuan sesi
Flash firmware, kalibrasi dasar, dan memutar motor untuk pertama kali.

## Yang dikerjakan
- Flash **ArduCopter 4.7.1**, target **Pixhawk1** (ChibiOS) via QGroundControl. Flash size 2 MB, jadi bukan varian -1M. Varian bdshot dilewati demi kesederhanaan.
- Frame Quad X, kalibrasi accelerometer dan kompas.
- Output motor dipindah ke AUX 1–4 dengan DShot600.
- `ARMING_SKIPCHK` = 64 (lewati pengecekan RC saja) dan `FS_THR_ENABLE` = 0, karena belum punya RC.
- Motor test A–D: urutan salah, lalu diperbaiki. Lihat [decisions/003](../decisions/003-remap-motor-via-servo-function.md).
- Arah putaran motor diperbaiki. Lihat [failures/002](../failures/002-dshot-dan-rvmask-tidak-aktif.md).

## Yang dipelajari
- Safety switch mengunci output, dan otomatis terkunci lagi setiap reboot.
- ESC mendeteksi protokol (PWM vs DShot) hanya saat pertama dinyalakan, jadi perubahan `MOT_PWM_TYPE` butuh cabut-pasang baterai, bukan sekadar reboot Pixhawk.
- Bootloader melaporkan Board ID 255 (ciri klon), tapi flashing tetap berhasil.
- Baris `RCOut:` di Vehicle Messages adalah cara tercepat memastikan DShot benar-benar aktif.

## Next step
Kalibrasi power module, failsafe, joystick.
