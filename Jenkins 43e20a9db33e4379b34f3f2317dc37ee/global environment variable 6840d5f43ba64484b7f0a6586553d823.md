# global environment variable

kita bisa menambahkan environment variable tambahan ke jenkins, environment variable yang kita tambahkan secara otomatis akan teregistrasi secara global, dan bisa digunakan di semua job

fitur ini sangat cocok ketika kita butuh data konfigurasi yang bisa diubah-ubah, tanpa harus mengubah build step setiap job yang kita buat.

untuk mengubah environment variable, kita bisa menggunakan menu manage jenkins > configure system > global properties > environment variable

contoh : 

![Untitled](global%20environment%20variable%206840d5f43ba64484b7f0a6586553d823/Untitled.png)