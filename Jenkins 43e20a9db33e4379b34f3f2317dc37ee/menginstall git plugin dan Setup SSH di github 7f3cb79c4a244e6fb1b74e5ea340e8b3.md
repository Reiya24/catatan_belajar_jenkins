# menginstall git plugin dan Setup SSH di github

setelah menginstall git plugin, maka kita bisa menambahkan sumber kode dari git repository di job yang sudah kita buat

pada dashboard, pilih manage jenkins

![Untitled](menginstall%20git%20plugin%20dan%20Setup%20SSH%20di%20github%207f3cb79c4a244e6fb1b74e5ea340e8b3/Untitled.png)

pilih manage plugin

![Untitled](menginstall%20git%20plugin%20dan%20Setup%20SSH%20di%20github%207f3cb79c4a244e6fb1b74e5ea340e8b3/Untitled%201.png)

pilih available

![Untitled](menginstall%20git%20plugin%20dan%20Setup%20SSH%20di%20github%207f3cb79c4a244e6fb1b74e5ea340e8b3/Untitled%202.png)

direkomendasikan untuk mengklik check now untuk merefresh daftar plugin yang tersedia

![Untitled](menginstall%20git%20plugin%20dan%20Setup%20SSH%20di%20github%207f3cb79c4a244e6fb1b74e5ea340e8b3/Untitled%203.png)

kita bisa menggunakan fitur pencarian untuk mencari git plugin, lalu pilih download now and install after restart

![Untitled](menginstall%20git%20plugin%20dan%20Setup%20SSH%20di%20github%207f3cb79c4a244e6fb1b74e5ea340e8b3/Untitled%204.png)

jenkins akan menginstall plugin git, dan menginstall depensi plugin lain yang diperlukan

![Untitled](menginstall%20git%20plugin%20dan%20Setup%20SSH%20di%20github%207f3cb79c4a244e6fb1b74e5ea340e8b3/Untitled%205.png)

setelah proses instalasi selesai, klik restart jenkins agar jenkins melakukan restart secara otomatis jika tidak ada jobs yang berjalan

![Untitled](menginstall%20git%20plugin%20dan%20Setup%20SSH%20di%20github%207f3cb79c4a244e6fb1b74e5ea340e8b3/Untitled%206.png)

## setup SSH di github

pada kasus ini, kita akan menggunakan github sebagai git repository, oleh karena itu, kita perlu melakukan setup github terlebih dahulu, agar jenkins bisa mengambil kode program di github

copy public ssh yang sudah di generate di server, lalu paste di di akun github kita, dengan masuk ke menu setting > SSH and GPG keys > lalu klik new SSH key, atau masuk ke halaman berikut [https://github.com/settings/ssh/new](https://github.com/settings/ssh/new)

![Untitled](menginstall%20git%20plugin%20dan%20Setup%20SSH%20di%20github%207f3cb79c4a244e6fb1b74e5ea340e8b3/Untitled%207.png)