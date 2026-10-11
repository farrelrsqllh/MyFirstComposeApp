# Homework 6 — My First Compose App

## Task 3: Colour and Spacing
Colour used: Color.Yellow
Padding kept: 8.dp
What changed / what stayed the same: Saat padding diubah dari 8.dp ke 48.dp, jarak ruang kosong antara pinggiran layar dengan konten menjadi lebih besar (konten terdorong ke tengah). Yang tetap sama adalah ukuran gambar, teks, dan struktur susunan vertikalnya.

## Task 4: Build Error
First error message:
`'My-Picture.png' is not a valid file-based resource name character: File-based resource names must contain only lowercase a-z, 0-9, or underscore.`
Cause: Aturan penamaan file sumber daya (resource/drawable) di Android sangat ketat. File hanya boleh menggunakan huruf kecil (lowercase), angka, dan garis bawah (_). Penggunaan huruf kapital dan tanda hubung pada `My-Picture.png` melanggar aturan ini.
Why other errors appear: Karena gambar gagal diproses dan ditolak oleh sistem, Android Studio tidak dapat membuat ID untuk gambar tersebut di class `R`. Akibatnya, baris kode di Kotlin yang memanggil gambar tersebut menjadi error (unresolved reference) karena ID-nya dianggap tidak ada.
Fix: Mengubah kembali nama file gambar tersebut menjadi huruf kecil semua tanpa tanda hubung, yaitu `my_picture.png`.

## Task 5: Explore the Project
(a) MainActivity: path `app/src/main/java/com/example/myfirstcomposeapp/MainActivity.kt` — Ini adalah titik masuk (entry point) utama dari aplikasi Android yang bertugas menampilkan antarmuka pengguna (UI) ke layar.
(b) Gradle file: path `app/build.gradle.kts` — File ini digunakan untuk mengatur konfigurasi *build* dan mendaftarkan *library* atau dependensi khusus untuk modul aplikasi.
(c) Launcher image line: `painter = painterResource(id = R.drawable.ic_launcher_foreground)` — Baris kode ini berfungsi untuk memuat dan menampilkan file sumber daya gambar bawaan Android (ikon launcher) ke dalam aplikasi.

## Task 6: Preview vs Run
Me-refresh Preview hanya memerintahkan Android Studio untuk merender ulang fungsi Composable secara visual di dalam layar editor komputer. Aplikasi di perangkat (HP/Emulator) tidak akan ikut berubah karena sistem belum menyatukan (compile) kode baru tersebut menjadi file APK. Langkah yang diperlukan agar perubahan muncul di perangkat adalah menekan tombol **Run**, yang akan melakukan *build* ulang APK dari kode terbaru dan menginstalnya kembali ke dalam perangkat.

## Task 7: Views vs Compose
1. Pendekatan **imperative (Views)** mengharuskan kita mencari komponen UI secara manual (misal lewat `findViewById`) lalu mengubah kondisinya langkah demi langkah (misal `textView.text = "Hello"`). Sedangkan pendekatan **declarative (Compose)**, seperti pada `MyFirstScreen`, kita hanya perlu mendeskripsikan secara langsung bagaimana bentuk UI seharusnya menggunakan fungsi Kotlin, dan UI akan otomatis menyesuaikan diri tanpa perlu kita atur ulang secara manual saat datanya berubah.
2.
| Composable | Package | Library layer |
|---|---|---|
| Column | `androidx.compose.foundation.layout` | Foundation |
| Text | `androidx.compose.material3` | Material |
| Image | `androidx.compose.foundation` | Foundation |