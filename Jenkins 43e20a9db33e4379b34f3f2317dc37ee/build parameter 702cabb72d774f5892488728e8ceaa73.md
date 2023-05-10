# build parameter

adalah fitur dimana kita bisa meminta input data dari user sebelum menjalankan jobnya, terdapat banyak sekali jenis input data, seperti boolean, string, choice, secret dan lain-lain.

semua input yang diberikan oleh user, secara otomatis bisa kita ambil seperti environment variable di build step. 

untuk menambahkan parameter, pada konfigurasi job kita, ceklis “this project is parameterized”, lalu tambahkan parameter

![Untitled](build%20parameter%20702cabb72d774f5892488728e8ceaa73/Untitled.png)

contoh penggunaan pada job belajar jenkins :

![Untitled](build%20parameter%20702cabb72d774f5892488728e8ceaa73/Untitled%201.png)

sekarang, saat kita ingin melakukan build, akan diminta pilihan yang sudah kita deklarasikan tadi

![Untitled](build%20parameter%20702cabb72d774f5892488728e8ceaa73/Untitled%202.png)