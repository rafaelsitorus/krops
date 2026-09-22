# Wiring

## Pinout ESC 4-in-1 (stack Velox F722), soket 10-pin 1,25 mm

| Pin | Fungsi | Tujuan |
|---|---|---|
| 1 | GND | Rail GND AUX (baris bawah) |
| 2 | GND | Diisolasi |
| 3 | VBAT | **Diisolasi rapat** |
| 4 | 10V | Diisolasi |
| 5 | M4 | AUX 4 Signal |
| 6 | M2 | AUX 2 Signal |
| 7 | M3 | AUX 3 Signal |
| 8 | M1 | AUX 1 Signal |
| 9 | CUR | Diisolasi (opsional untuk sensor arus) |
| 10 | TX | Diisolasi (opsional untuk telemetri ESC) |

Rail AUX Pixhawk: baris atas = Signal, tengah = +5V (tidak dipakai), bawah = GND.

## Jalur daya
Baterai → XT60 → Power Module (port POWER Pixhawk) → XT60 → ESC 4-in-1.
PDB belum dipakai. Kalau ditambahkan nanti untuk aksesori, letakkan **setelah** power module.

## Komponen
- Flight controller: Pixhawk 2.4.8
- ESC: 4-in-1 dari stack Velox F722 (BLHeli_32)
- Power module, safety switch, PDB + XT60
- Toolkit (belum dipakai di pipeline): UBEC Bluesky, USB-to-TTL, logic analyzer 8-bit, ST-Link V2
