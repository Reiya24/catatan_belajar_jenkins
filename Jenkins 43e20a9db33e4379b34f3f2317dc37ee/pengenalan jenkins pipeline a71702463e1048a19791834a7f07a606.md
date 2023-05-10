# pengenalan jenkins pipeline

jenkins pipeline merupakan plugin yang mendukung implementasi pembuatan continous delivery pipeline di jenkins, contiunous delivery pipeline adalah script yang dibuat agar software yang kita buat bisa di deliver ke pengguna, mulai dari version control sampai deployment.

jenkins pipeline menggunakan bahasa pemrograman groovy sebagai (DSL) nya

## kenapa pipeline

karena pipeline dibuat menggunakan kode, sehingga kita bisa dengan mudah mengubah / mereview tahapan pipeline.

pipeline dibuat dalam file dan disimpan di projectnya, maka tidak perlu takut hilang ketika terjadi restart / kerusakan di jenkins nya.

kita bisa memasukan logic yang sederhana sampai kompleks di pipeline, seperti pengecekan kondisi, perulangan, dan lain-lain

## menggunakan pipeline

instal plugin pipeline, dan pipeline:stage view terlebih dahulu sebelum menggunakan pipeline

![Untitled](pengenalan%20jenkins%20pipeline%20a71702463e1048a19791834a7f07a606/Untitled.png)