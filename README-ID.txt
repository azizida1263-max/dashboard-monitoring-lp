# PWA Dashboard Monitoring LP

Paket ini adalah PWA wrapper untuk dashboard Google Apps Script yang sudah berjalan.
URL dashboard yang ditautkan:
https://script.google.com/macros/s/AKfycbxt0GVYu6Dqa-_xTfKA6NAuKQ6qJ8uA9lkU9BBa__2XABpu6p94dDAAJdC1p9WpnhgZ/exec

## Isi paket
- `index.html`: layar aplikasi PWA, menampilkan dashboard di dalam iframe.
- `manifest.webmanifest`: identitas dan pengaturan instalasi PWA.
- `sw.js`: service worker untuk menyimpan shell PWA saja.
- `icons/`: ikon aplikasi 192 dan 512 px.
- `android-wrapper/`: contoh proyek Android WebView untuk membungkus alamat PWA setelah hosting tersedia.

## Cara memasang PWA
1. Upload seluruh isi folder ini ke hosting HTTPS yang mendukung file statis (contoh: GitHub Pages atau Firebase Hosting).
2. Pastikan `index.html`, `manifest.webmanifest`, `sw.js`, dan folder `icons` berada pada satu direktori.
3. Buka alamat hosting dari Chrome Android.
4. Pilih menu Chrome > **Install app / Tambahkan ke layar utama** atau tekan tombol **Pasang APP** jika muncul.
5. Login Google bila dashboard meminta autentikasi.

## Penting
- Dashboard tetap mengambil data dari Google Sheets melalui Google Apps Script.
- Service Worker hanya menyimpan file pembungkus PWA. Data dashboard tidak disimpan offline agar data tetap akurat dan tidak membocorkan data akun.
- PWA memerlukan koneksi internet untuk memuat dashboard dan data.
- Pastikan deployment Apps Script tetap dapat diakses oleh akun pengguna yang dituju. Jangan mengubah izin menjadi publik tanpa mempertimbangkan kebijakan data perusahaan.
- Jika iframe ditolak oleh kebijakan login atau browser, solusi berikutnya adalah menjadikan tampilan HTML sebagai frontend yang di-host langsung dan memindahkan endpoint data secara terkontrol; jangan menonaktifkan keamanan akun.

## APK Android
Folder `android-wrapper` berisi kerangka WebView. Setelah PWA di-host:
1. Ganti `PWA_HOST_URL` di `MainActivity.kt` dengan URL HTTPS hosting PWA.
2. Buka folder `android-wrapper` melalui Android Studio.
3. Build > Build Bundle(s) / APK(s) > Build APK(s).
4. Uji APK pada HP Android dan pastikan alur login Google berfungsi.

APK belum berupa file instalasi final karena alamat hosting PWA belum ditentukan dan proses signing/build Android harus dilakukan setelah URL hosting tersedia.
