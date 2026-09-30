# 002: DShot dan SERVO_BLH_RVMASK tidak berefek

**Tanggal:** 2026-09-22

## Apa yang terjadi
Dua kegagalan berurutan saat motor test:
1. Motor test "berjalan" (log: starting/finished) tapi motor diam.
2. Setelah DShot aktif, arah motor tidak mau dibalik walaupun `SERVO_BLH_RVMASK` sudah diisi dan tersimpan.

## Akar masalah
1. `MOT_PWM_TYPE` belum tersimpan; baris `RCOut: PWM:1-14` menunjukkan semua output masih PWM. Setelah diperbaiki: `RCOut: PWM:1-8 DS600:9-12`.
2. Dua sebab bertumpuk:
   - ESC mendeteksi protokol hanya saat **pertama dinyalakan**. Reboot Pixhawk lewat USB tidak mematikan ESC (dayanya dari baterai), jadi ESC masih menunggu PWM.
   - `SERVO_BLH_RVMASK` dikirim sebagai perintah khusus DShot, dan perintah itu hanya dikirim kalau **`SERVO_DSHOT_ESC`** diset (BLHeli32). Dengan nilai default None, RVMASK tersimpan tapi tidak pernah sampai ke ESC.

## Pelajaran
- Verifikasi protokol dari baris `RCOut:` di Vehicle Messages, jangan dari nilai parameter saja.
- Urutan menyalakan penting: ESC harus sudah hidup saat Pixhawk booting agar perintah DShot diterima.
- `SERVO_BLH_RVMASK` dan `SERVO_BLH_AUTO` tidak cukup tanpa `SERVO_DSHOT_ESC`.
