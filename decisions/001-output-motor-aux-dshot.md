# 001: Output motor di AUX 1–4 dengan DShot

**Tanggal:** 2026-09-22 · **Status:** Diterapkan (wiring), parameter menunggu motor test

## Konteks
Pixhawk 2.4.8 punya dua rail output: MAIN OUT 1–8 dan AUX OUT 1–6.

## Opsi
1. **MAIN OUT + PWM**: kompatibel dengan semua firmware, tapi wajib kalibrasi ESC.
2. **AUX OUT + DShot**: tanpa kalibrasi, sinyal digital lebih presisi dan tahan noise, mendukung BLHeli passthrough dan membuka jalan untuk telemetri ESC.

## Keputusan
AUX + DShot. MAIN OUT dikendalikan IO co-processor (STM32F100) yang hanya bisa PWM; AUX langsung dari FMU (STM32F427) yang mendukung DShot.

## Konsekuensi
- Parameter: `SERVO9–12_FUNCTION` = 33–36, `SERVO1–4_FUNCTION` = 0, `MOT_PWM_TYPE` = DShot300/600, `SERVO_BLH_AUTO` = 1.
- Label M1–M4 di ESC mengikuti Betaflight, jadi urutan motor harus diverifikasi via motor test.
- Fallback kalau firmware lama tidak mendukung: pindah ke MAIN + PWM.
