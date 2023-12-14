# Cara untuk menggunakan Aplikasi API Mahasiswa dengan Node.js dan MySQL

**File ini menjelaskan cara menjalankan aplikasi API untuk mengelola data mahasiswa menggunakan Node.js dan MySQL dalam lingkungan Docker.**

## Prasyarat
  * Docker Engine terinstal dan berjalan di komputer Anda.
  * Git terinstal dan digunakan untuk mengkloning repositori.
## Instalasi
  1. Kloning repositori ke direktori lokal Anda.
  2. Buka terminal dan navigasikan ke direktori repositori.
  3. Jalankan perintah berikut untuk membangun dan menjalankan image Docker:
  ```docker
  docker build -t mahasiswa-api .
  docker run -p 8000:8000 mahasiswa-api
  ```
## Konfigurasi database
  1. Ganti nilai `host`, `user`, `password`, dan `database` di file `app.js` sesuai dengan konfigurasi database MySQL Anda.
  2. Pastikan Anda memiliki tabel `mahasiswa` dengan kolom `id (integer, primary key)`, `nim (string)`, dan `nama (string)`.
