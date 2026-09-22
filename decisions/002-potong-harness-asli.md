# 002: Memotong harness JST-GH 10-pin asli

**Tanggal:** 2026-09-22 · **Status:** Diterapkan

## Konteks
ESC memakai soket 10-pin 1,25 mm, sedangkan output Pixhawk berupa header servo 2,54 mm. Harness bawaan 10-10 sangat pendek (±7–8 cm).

## Opsi
1. **Pigtail JST-GH 10-pin baru**: harness asli tetap utuh, tapi tidak tersedia di toko lokal.
2. **Pigtail JST-GH 5-pin** (satu-satunya stok lokal): ditolak, karena GND (pin 1–2) dan M1–M4 (pin 5–8) tidak berurutan sehingga tidak bisa dijangkau satu konektor 5-pin, dan housing tidak terkunci di soket 10-pin.
3. **Potong harness asli**, lalu sambung ke jumper Dupont female.

## Keputusan
Opsi 3. Konektornya sudah pasti cocok dengan soket ESC, dan jumper Dupont sekaligus menyelesaikan masalah panjang kabel.

## Konsekuensi
Harness asli tidak bisa lagi dipakai untuk kembali ke FC F722. Kalau perlu, pesan JST-GH 10-pin online.
