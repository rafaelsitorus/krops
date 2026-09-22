# 001: Konektor pengganti tidak cocok dengan soket ESC

**Tanggal:** 2026-09-22

## Apa yang terjadi
Rencana awal memakai pigtail JST-SH 1,0 mm untuk menyambung ESC ke Pixhawk. Ternyata soket ESC 1,25 mm (JST-GH), dan stok lokal hanya ada JST-GH 5-pin, sedangkan yang dibutuhkan 10-pin.

## Akar masalah
Pitch konektor diasumsikan tanpa diukur. Selisih pitch 1,0 vs 1,25 mm membuat konektor 10-pin berbeda lebar ±2,25 mm, sehingga tidak bisa masuk.

## Solusi
Memotong harness asli (lihat [decisions/002](../decisions/002-potong-harness-asli.md)).

## Pelajaran
- Ukur pitch dan hitung pin sebelum membeli konektor. Bawa konektor asli ke toko untuk dicocokkan.
- "1,25 mm" di toko bisa berarti JST-GH (ada kait pengunci) atau Molex PicoBlade (tanpa kait). Keduanya tidak kompatibel.
- Kabel DF13 6-pin bawaan kit Pixhawk bukan pengganti. Simpan untuk telemetri/GPS.
