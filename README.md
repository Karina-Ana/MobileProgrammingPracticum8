# Navigasi Argumen – Flutter

## 📝 Deskripsi Singkat

Aplikasi berbasis Flutter yang menerapkan navigasi antar halaman menggunakan **Named Route** dengan pengiriman argumen. Aplikasi mengambil informasi game dari API FreeToGame, menampilkan ringkasan game pada halaman Home, kemudian mengirimkan data ke halaman Tujuan untuk menampilkan detail game.

Data yang dikirim mencakup gambar cover, judul, deskripsi lengkap, dan deskripsi singkat. Pengiriman data dilakukan menggunakan objek `ScreenArguments`, sedangkan halaman tujuan mengaksesnya melalui `ModalRoute`.

## ✨ Fitur Utama

- **Halaman Home:** Menampilkan thumbnail, judul, genre, platform, publisher, dan tanggal rilis game.
- **Pengambilan Data API:** Mengambil informasi game dari FreeToGame menggunakan package `http`.
- **Navigasi Named Route:** Berpindah halaman menggunakan `Navigator.pushNamed()`.
- **Pengiriman Argumen:** Mengirim data game melalui parameter `arguments` dalam bentuk objek `ScreenArguments`.
- **Halaman Detail:** Menampilkan gambar cover, judul, dan deskripsi game.
- **Navigasi Kembali:** Menggunakan `Navigator.pop()` untuk kembali ke halaman Home.

## 🛠️ Teknologi yang Digunakan

- Flutter dan Dart
- Material Design
- Package `http` untuk mengambil data dari API
- API FreeToGame sebagai sumber informasi game

## 📂 Struktur Proyek

```text
navigasi_argumen/
├── lib/
│   ├── main.dart
│   ├── home.dart
│   ├── tujuan.dart
│   └── screen_arguments.dart
├── pubspec.yaml
└── README.md
```

- `main.dart`: Mengatur aplikasi, tema, halaman awal, dan daftar route.
- `home.dart`: Mengambil data game dari API dan menampilkan informasi ringkas pada halaman Home.
- `tujuan.dart`: Menampilkan detail game berdasarkan argumen yang diterima.
- `screen_arguments.dart`: Menyimpan data yang akan dikirim antar halaman melalui class `ScreenArguments`.

## 🌐 Sumber Data API

Aplikasi menggunakan API FreeToGame untuk mengambil informasi game berdasarkan ID.

Endpoint yang digunakan:

```text
https://www.freetogame.com/api/game?id=475
```

Data yang diambil meliputi judul, thumbnail, deskripsi singkat, deskripsi lengkap, genre, platform, publisher, tanggal rilis, dan gambar cover dari screenshot game.

## 🔄 Alur Kerja Aplikasi

1. Aplikasi dibuka dan menampilkan halaman Home.
2. Fungsi `getGame()` mengirim HTTP request ke API FreeToGame untuk mengambil informasi game.
3. Data respons JSON diproses dan disimpan dalam variabel aplikasi.
4. Halaman Home menampilkan ringkasan informasi game.
5. Saat item game ditekan, objek `ScreenArguments` dibuat untuk mengemas data yang akan dikirim.
6. `Navigator.pushNamed()` membuka halaman Tujuan sekaligus membawa argumen tersebut.
7. Halaman Tujuan mengambil data menggunakan `ModalRoute.of(context)!.settings.arguments` dan menampilkan detail game.
8. Tombol kembali menjalankan `Navigator.pop(context)` untuk kembali ke halaman Home.

## 📚 Konsep yang Dipelajari

### 1. Named Route

Named Route memungkinkan halaman dipanggil berdasarkan nama yang telah didaftarkan dalam properti `routes` pada `MaterialApp`.

### 2. ScreenArguments

`ScreenArguments` merupakan class yang digunakan untuk mengemas beberapa informasi game ke dalam satu objek agar dapat dikirim antar halaman.

### 3. Navigator.pushNamed()

Digunakan untuk membuka halaman berdasarkan nama route sekaligus mengirimkan data melalui parameter `arguments`.

### 4. ModalRoute

`ModalRoute` digunakan untuk mengakses argumen yang diterima oleh halaman tujuan melalui pengaturan route.

### 5. Navigator.pop()

Digunakan untuk menutup halaman detail dan kembali ke halaman sebelumnya.

### 6. HTTP Request dan JSON

Package `http` digunakan untuk mengambil data dari API, sedangkan `dart:convert` digunakan untuk mengolah respons JSON agar informasinya dapat ditampilkan pada antarmuka aplikasi.

## 🚀 Cara Menjalankan

1. Buka proyek Flutter melalui Android Studio atau VS Code.
2. Pastikan package `http` telah ditambahkan pada bagian `dependencies` di file `pubspec.yaml`.

   ```yaml
   dependencies:
     flutter:
       sdk: flutter
     http: ^1.5
   ```

3. Jalankan perintah berikut pada terminal:

   ```bash
   flutter pub get
   ```

4. Pastikan perangkat atau emulator memiliki koneksi internet untuk mengambil data dari API.
5. Jalankan aplikasi menggunakan tombol **Run** atau perintah:

   ```bash
   flutter run
   ```

6. Tunggu hingga informasi game tampil pada halaman Home, lalu tekan kartu game untuk membuka halaman detail.

## 🎯 Kesimpulan

Named Route memungkinkan navigasi antar halaman dilakukan secara terstruktur berdasarkan nama route. Dengan menggunakan `Navigator.pushNamed()` dan parameter `arguments`, data game dapat dikirim dari halaman Home ke halaman Tujuan melalui objek `ScreenArguments`. Selanjutnya, data tersebut diakses menggunakan `ModalRoute` dan ditampilkan sebagai informasi detail game dari API FreeToGame.
