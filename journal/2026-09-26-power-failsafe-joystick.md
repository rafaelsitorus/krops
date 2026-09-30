# 2026-09-26: Power module, failsafe, geofence, joystick

## Yang dikerjakan
- Kalibrasi tegangan power module. Lihat [failures/003](../failures/003-power-module-multiplier-non-standar.md).
- Battery: kapasitas 5200 mAh, Low 10,5 V → RTL, Critical 9,9 V → Land (baterai 3S). mAh threshold dibiarkan 0 sampai sensor arus dikalibrasi.
- Ground Station Failsafe. Lihat [decisions/005](../decisions/005-gcs-failsafe-tanpa-rc.md).
- Geofence aktif: max altitude 15 m, circle radius 30 m, margin 2 m, breach action RTL or Land, auto-enable saat arm.
- Joystick dikalibrasi dan tombol dipetakan (arm, disarm, AltHold, Loiter, Land, RTL). Lihat [decisions/004](../decisions/004-joystick-via-telemetri.md).

## Yang dipelajari
- Motor 2216 880KV + propeller 1045 + 3S adalah kombinasi yang sesuai; kekhawatiran awal soal kurang daya tidak terbukti.
- Mur propeller yang mengendur saat motor berhenti = propeller terpasang di motor dengan arah putaran yang salah. Mur mengunci sendiri oleh putaran, jadi ini indikator paling andal.
- "Potential Thrust Loss" wajar kalau propeller belum terpasang.
- Tombol Takeoff memindahkan mode ke Guided, bukan cara yang tepat untuk penerbangan manual pertama.
- Home position ditetapkan saat arm; berpindah lokasi tanpa cabut-pasang baterai membuat fence menolak arm.

## Next step
Terbang manual, lalu waypoint.
