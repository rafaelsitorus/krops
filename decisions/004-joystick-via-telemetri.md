# 004: Gamepad via telemetri sebagai kendali manual sementara

**Tanggal:** 2026-09-26 · **Status:** Diterapkan

## Konteks
Belum punya RC transmitter. Pilihannya: terbang tanpa kendali manual sama sekali (hanya misi otomatis), atau memakai gamepad yang perintahnya dikirim lewat radio telemetri.

## Keputusan
Gamepad via telemetri, sambil menabung untuk RC.

## Alasan
Masalah khas penerbangan awal (tuning, vibrasi, kompas) terjadi **di dalam** batas geofence, dan fence tidak melindungi dari itu. Yang dibutuhkan adalah kemampuan berpindah ke AltHold atau Land saat drone berperilaku aneh.

## Konsekuensi
- Kendali dan telemetri berbagi satu jalur, jadi link putus = kendali hilang. Karena itu GCS failsafe wajib aktif; lihat [005](005-gcs-failsafe-tanpa-rc.md).
- Stik gamepad kembali ke tengah saat dilepas, sehingga **Stabilize tidak boleh dipakai** (tengah = throttle 50%). Terbang manual selalu di AltHold atau Loiter.
- `ARMING_SKIPCHK` = 64 dipertahankan selama belum ada receiver RC.
