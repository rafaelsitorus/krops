# 005: GCS failsafe SmartRTL/Land, "in pilot control" dimatikan

**Tanggal:** 2026-09-26 · **Status:** Diterapkan

## Konteks
Kendali manual berjalan lewat telemetri (lihat [004](004-joystick-via-telemetri.md)), jadi tidak ada jalur cadangan kalau link putus.

## Keputusan
- `FS_GCS_ENABLE` aktif, action **SmartRTL or Land**, timeout 5 detik.
- Opsi **"ignore failsafe in pilot control" dimatikan.**
- Opsi "ignore in Auto mode" juga dimatikan.

## Alasan
Default ArduPilot mengabaikan GCS failsafe saat pilot sedang memegang kendali, karena mengasumsikan pilot punya RC sebagai cadangan. Asumsi itu tidak berlaku di sini: saat link putus, justru tidak ada yang mengendalikan drone.

## Konsekuensi
Kalau telemetri putus >5 detik, drone pulang atau mendarat sendiri, termasuk saat sedang diterbangkan manual. Ini disengaja.
