# discard old buildl

jenkis menyimpan semua history build di folder .jenkins di HOME directory, secara default, jenkkins akan menyimpan semua history jjob selamanya, hal ini tidak baik karena lama lama server jenkins kita bisa jadi kehabisan ruang penyimpanan.

jenkins memiliki fitur penghapusan riwayat build yang lama secara otomatis, baik itu menggunakan hari atau jumlah build, ketika kita menambahkan atuan ini, secara otomatis jenkins akan melakukan pengecekan ketika selesaai menjalankan job.

untuk melakukan penghapusan old build, ceklis discard old build, lalu sesuaikan konfigurasi

![Untitled](discard%20old%20buildl%2069203b9699154f8bbe7eee24135f9909/Untitled.png)