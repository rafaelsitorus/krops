# 003: Power module dengan pembagi tegangan non-standar

**Tanggal:** 2026-09-26

## Apa yang terjadi
Pembacaan tegangan baterai meleset jauh. Dengan `BATT_VOLT_MULT` = 9,23 (nilai yang dihitung dari asumsi default 10,1), QGroundControl menampilkan 5,34 V padahal multimeter menunjukkan 12,68 V. Sebelumnya sempat terbaca 0,03 V, sehingga pre-arm menolak dengan "Battery below minimum arming voltage".

## Akar masalah
Power module klon bawaan kit memakai rasio pembagi tegangan yang jauh dari standar Pixhawk. Nilai yang benar ternyata **21,9**, lebih dari dua kali nilai default.

Diagnosis sempat salah arah: nilai di luar rentang "wajar" 9–12 diasumsikan hasil perhitungan yang keliru, padahal memang segitu nilainya untuk modul ini.

## Pelajaran
- Untuk power module non-standar, rentang nilai "wajar" tidak berlaku. Patokannya hanya satu: pembacaan cocok dengan multimeter.
- Verifikasi di **dua titik tegangan berbeda** untuk memastikan hubungannya linear, bukan kebetulan pas di satu titik.
- `BATT_ARM_VOLT` jangan disamakan dengan threshold Low failsafe; beri jarak (11,1 V vs 10,5 V untuk 3S).
