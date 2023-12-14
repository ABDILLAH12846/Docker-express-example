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

## Penggunaan API
Aplikasi ini menyediakan endpoint untuk mengelola data mahasiswa:
  * **GET /**: Mendapatkan semua data mahasiswa.
  * **POST /**: Menambahkan data mahasiswa baru.
    * Body request harus berupa JSON dengan key `nim` dan `nama`.
  * **PUT /:id**: Memperbarui data mahasiswa berdasarkan ID.
    * Body request harus berupa JSON dengan key `nim` dan `nama`.
    * Parameter URL `:id` harus diisi dengan ID mahasiswa yang ingin diperbarui.
  * **DELETE /:id**: Menghapus data mahasiswa berdasarkan ID.
    * Parameter URL `:id` harus diisi dengan ID mahasiswa yang ingin diperbarui.

 ## Contoh penggunaan API
   1. Mendapatkan semua data mahasiswa:
      ```curl
      curl http://localhost:8000/
      ```
      Respon:
      ```json
      [
        { "id": 1, "nim": "12345678", "nama": "John Doe" },
        { "id": 2, "nim": "98765432", "nama": "Jane Doe" }
      ]
      ```
   2. Menambahkan data mahasiswa baru:
      ```curl
      curl -X POST -H "Content-Type: application/json" -d '{"nim": "00987654", "nama": "Alice Smith"}' http://localhost:8000/
      ```
      Respon:
      ```json
      { "message": "Data mahasiswa berhasil ditambahkan", "id": 3 }
      ```
   3. Memperbarui data mahasiswa dengan ID 2:
      ```curl
      curl -X PUT -H "Content-Type: application/json" -d '{"nim": "987654321", "nama": "Jane Doe Update"}' http://localhost:8000/2
      ```
      Respon:
      ```json
      { "message": "Data mahasiswa berhasil diperbarui" }
      ```
   4. Menghapus data mahasiswa dengan ID 1:
      ```curl
      curl -X DELETE http://localhost:8000/1
      ```
      Respon:
      ```json
      { "message": "Data mahasiswa berhasil dihapus" }
      ```
## Catatan:
  * Pastikan Anda telah mengganti informasi konfigurasi database sebelum menjalankan aplikasi.
  * Untuk mengakses API dari aplikasi lain, Anda dapat menggunakan library HTTP client seperti Axios atau Request.
## Kontribusi:
  * Silakan ajukan issue atau pull request jika Anda menemukan bug atau ingin menambahkan fitur baru ke aplikasi ini.


**Semoga readme.md ini membantu Anda dalam menjalankan dan menggunakan aplikasi API mahasiswa!**
