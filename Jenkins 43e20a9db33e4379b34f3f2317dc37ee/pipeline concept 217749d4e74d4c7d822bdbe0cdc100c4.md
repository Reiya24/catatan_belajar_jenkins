# pipeline concept

## pipeline

pipeline adalah definisi kode continuous delivery, misal seperti compile, testing, deploy, dan lain-lain. kode pipeline menggunakan kata kunci pipeline

## agent

agent adalah machine/server bagian dari jenkins yang digunakan untuk mengeksekusi pipeline, kode penentuan agent menggunakan kata kunci agent, agent disebutkan di dalam kode pipeline yang kita buat

## stage

stage adalah blok definisi tugas atau tahapan dalam pipeline, misalnya “build”, “test”, “deploy”, dan lain lain, stage biasanya ditampilkan di jenkins seperti tahapan progress dari pipeline, biasanya dalam pipeline, akan terdapat banyak stage, stage menggunakan kata kunci stage

## step

adalah sebuah instruksi/ perintah yang harus dilakukan oleh jenkins, step dilakukan di dalam stage, step menggunakan kata kunci steps

## contoh pipeline

![Untitled](pipeline%20concept%20217749d4e74d4c7d822bdbe0cdc100c4/Untitled.png)