# 2026-09-22: Perakitan, wiring ESC, dan setup software

## Tujuan sesi
Menyambungkan ESC 4-in-1 (stack Velox F722) ke Pixhawk 2.4.8 dan menyiapkan software di Mac.

## Yang dikerjakan
- Memetakan pinout ESC 10-pin (lihat [hardware/wiring.md](../hardware/wiring.md)).
- Memotong harness 10-pin asli, menyambung 5 kabel (GND, M1–M4) ke jumper Dupont female, mengisolasi 5 kabel sisanya.
- Mencolok sinyal motor ke AUX 1–4 dan GND ke rail AUX. Lihat [decisions/001](../decisions/001-output-motor-aux-dshot.md).
- Setup software macOS: QGroundControl, BLHeliSuite32 (passthrough), SITL (build ArduPilot dari source), konfigurasi radio SiK via AT command.

## Masalah & solusi
- Konektor pengganti tidak cocok dengan soket ESC. Lihat [failures/001](../failures/001-konektor-harness-tidak-cocok.md) dan [decisions/002](../decisions/002-potong-harness-asli.md).

## Yang dipelajari
- Safety switch bukan tombol power: fungsinya mengunci/membuka output motor. Drone dimatikan dengan disarm lalu cabut baterai.
- MAIN OUT Pixhawk 2.4.8 dikendalikan IO co-processor (hanya PWM). DShot hanya tersedia di AUX.
- PDB tidak diperlukan untuk wiring dasar karena ESC 4-in-1 sudah membagi daya. PDB berguna nanti untuk aksesori (dipasang setelah power module).
- OLED opsional, ditunda.

## Open items
- Jalur kendali manual (RC vs gamepad via telemetri) belum diputuskan.
- Aksi failsafe telemetri putus belum difinalkan (kandidat: SmartRTL→Land atau Land).

## Bukti
- [ ] Foto wiring AUX & isolasi kabel
- [ ] Screenshot versi firmware / QGroundControl

## Next step
Flash/cek firmware ArduCopter → frame Quad X → kalibrasi → set output DShot → motor test tanpa propeller → export `.param` pertama.
