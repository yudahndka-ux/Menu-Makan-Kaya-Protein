# Menu Hemat Tinggi Protein

Aplikasi web sederhana (PWA, tanpa framework dan tanpa server) untuk merencanakan menu makan harian yang hemat, tinggi protein, dan mudah dimasak di rumah.

## Fitur
- Atur total budget, jumlah hari (1-7), dan target protein per hari.
- Harga disesuaikan per provinsi (38 provinsi) dan bisa diubah manual per bahan.
- Pilih menu tiap waktu makan, atau klik **Susun otomatis sesuai budget**.
- Buat, ubah, dan hapus menu serta bahan sendiri (menu "Menu Saya").
- Daftar belanja total atau per hari.
- Cetak rencana menu dan daftar belanja (tombol **Cetak**).
- Bisa dipasang di HP dan berjalan offline (PWA). Data tersimpan di browser (localStorage).

## Menjalankan
Buka `index.html` di browser, atau jalankan server lokal agar fitur PWA aktif:

```bash
python3 -m http.server 8000   # lalu buka http://localhost:8000
```

## Deploy ke GitHub Pages
1. Unggah semua file ke repositori GitHub.
2. Settings > Pages > Deploy from a branch > pilih `main` dan folder `/ (root)`.
3. Buka tautan Pages, lalu pilih "Pasang aplikasi" / "Tambahkan ke layar utama".

## Struktur file
| File | Fungsi |
|---|---|
| `index.html` | Seluruh aplikasi (HTML, CSS, JavaScript) |
| `manifest.json` | Metadata PWA |
| `sw.js` | Service worker untuk mode offline (naikkan `CACHE` setiap ada perubahan) |
| `icon.svg`, `icon-192.png`, `icon-512.png` | Ikon aplikasi |

## Tentang data
- Harga dasar adalah perkiraan pasar Jawa Barat. Indeks harga provinsi adalah **perkiraan kasar, bukan data resmi**. Sesuaikan harga atau rujuk sumber resmi seperti PIHPS (Bank Indonesia).
- Nilai protein adalah estimasi bahan mentah. Aplikasi ini bukan pengganti saran dokter atau ahli gizi.

## Kontribusi
Pull request dipersilakan: menambah menu, bahan, memperbaiki indeks harga provinsi, atau terjemahan.
Data bahan (`I`), menu (`M`), dan indeks provinsi (`PVS`) ada di bagian atas `<script>` di `index.html`.

## Lisensi
[MIT](LICENSE)

## Cadangan data
Menu **Harga** > **Unduh cadangan** menyimpan menu, bahan, harga, dan pengaturan ke file JSON. Pulihkan dengan memilih file itu di bagian yang sama.

## Jadi aplikasi Android (APK)
Ada dua cara, keduanya tanpa perlu Android Studio:

1. **GitHub Actions (sudah disiapkan).** Di GitHub buka tab *Actions* > *Build Android APK* > *Run workflow*. Setelah selesai, unduh `menu-hemat-apk` dari bagian *Artifacts*, lalu pasang `app-debug.apk` di HP (izinkan pemasangan dari sumber tidak dikenal). Ini APK debug; untuk Google Play perlu APK/AAB yang ditandatangani. Ubah `appId` di `capacitor.config.json` sesuai milik Anda.
2. **PWABuilder.** Setelah situs ada di GitHub Pages, masukkan alamatnya di pwabuilder.com untuk membuat paket Android/iOS/Windows.

Pengembangan lokal: `npm install`, `npm run android:add`, lalu buka folder `android/` dengan Android Studio.
