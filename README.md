
# CoroutineDemo

Aplikasi Android sederhana yang dibuat untuk memenuhi tugas praktikum Modul M17 – Coroutines and Asynchronous Programming.

## Deskripsi

Aplikasi ini menerapkan konsep Kotlin Coroutines untuk menjalankan proses asynchronous, mengambil data tugas, menangani loading, error, pembatalan proses, dan pengurutan data.

## Fitur Aplikasi

- Menampilkan daftar tugas.
- Menampilkan indikator loading saat mengambil data.
- Menangani error ketika proses pengambilan data gagal.
- Menyediakan tombol Retry untuk mencoba kembali.
- Membatalkan proses menggunakan Coroutine.
- Mengurutkan daftar tugas berdasarkan judul.
- Mengambil jumlah course secara asynchronous.
- Menjaga UI tetap responsif selama proses berjalan.

## Pengembangan Aplikasi

Pengembangan dilakukan berdasarkan materi Modul M17 dengan beberapa penambahan:

1. Menambahkan fungsi `getCourseCount()`.
2. Menggunakan `async` dan `await` untuk mengambil data secara bersamaan.
3. Menambahkan tombol Retry ketika terjadi error.
4. Menambahkan fitur pengurutan tugas berdasarkan judul.
5. Menerapkan `withContext(Dispatchers.IO)` untuk proses I/O.
6. Menguji perilaku cancellation dan dampak blocking pada Main Thread.

## Latihan 9

### 1. Perbedaan launch dan async

- `launch` digunakan untuk menjalankan coroutine tanpa mengembalikan hasil data secara langsung. Hasilnya berupa `Job`.
- `async` digunakan untuk menjalankan coroutine yang menghasilkan nilai. Hasilnya dapat diambil menggunakan `await()` melalui `Deferred`.

### 2. Mengapa GlobalScope tidak disarankan?

Karena GlobalScope tidak terikat dengan lifecycle komponen Android. Coroutine dapat tetap berjalan meskipun layar sudah ditutup sehingga berpotensi menggunakan sumber daya secara tidak perlu.

### 3. Apa yang terjadi ketika salah satu coroutine gagal?

Dalam `coroutineScope`, ketika salah satu child coroutine gagal, child coroutine lainnya akan dibatalkan. Exception kemudian diteruskan ke blok penanganan error.

### 4. Perbedaan Thread.sleep dan delay

- `delay()` menangguhkan coroutine tanpa memblokir thread.
- `Thread.sleep()` memblokir thread selama waktu yang ditentukan.

Pengujian menunjukkan bahwa `Thread.sleep()` di `Dispatchers.IO` tidak membekukan UI, sedangkan pemanggilan blocking pada Main Thread membuat UI tidak responsif sementara.

### 5. Bagaimana cancellation ditangani?

Cancellation merupakan bagian dari mekanisme coroutine. Jika menggunakan `catch (Exception)`, pembatalan dapat ikut tertangkap sebagai error. Karena itu, penanganan exception perlu memperhatikan `CancellationException`.

## Teknologi

- Kotlin
- Android Studio
- Jetpack Compose
- Kotlin Coroutines
- ViewModel
- StateFlow

## Author

Muhammad Thaahir Ramadhan
