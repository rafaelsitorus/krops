# 003: Remap motor lewat SERVOx_FUNCTION, bukan tukar kabel

**Tanggal:** 2026-09-22 · **Status:** Diterapkan

## Konteks
Motor test menunjukkan posisi A dan D tertukar. Label M1–M4 di ESC mengikuti penomoran Betaflight, yang berbeda dari urutan motor ArduPilot.

## Opsi
1. Tukar kabel Dupont di AUX 1 dan AUX 3.
2. Remap lewat parameter: `SERVO9_FUNCTION` = 35 (Motor3), `SERVO11_FUNCTION` = 33 (Motor1).

## Keputusan
Opsi 2. Wiring fisik sudah rapi dan konsisten dengan label ESC; yang tidak cocok adalah konvensi penomoran, bukan pemasangan kabel.

## Konsekuensi
- Nomor tombol motor test (A–D) tidak lagi sejajar dengan nomor port AUX. Saat mengatur `SERVO_BLH_RVMASK`, patokannya adalah **port AUX**, bukan huruf tombol: A→AUX 3, B→AUX 4, C→AUX 2, D→AUX 1.
- Pemetaan ini harus ikut dibaca bersama tabel di `hardware/wiring.md`.
