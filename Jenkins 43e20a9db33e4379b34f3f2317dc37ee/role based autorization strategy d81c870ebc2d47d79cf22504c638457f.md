# role based autorization strategy

secara default, jenkins tidak memiliki setelan untuk membatasi akses suatu user, namun kita bisa mengakalinya dengan menggunakan plugin role based authorization strategy

setelah menginstall plugin, kita perlu konfigurasi authorization menggunakan plugin yang sudah di install, pada menu manage jenkins > configure global security > authorization ubah ke role-based strategy

![Untitled](role%20based%20autorization%20strategy%20d81c870ebc2d47d79cf22504c638457f/Untitled.png)

lalu untuk manage dan assign role terdapat di setelan manage jenkins

![Untitled](role%20based%20autorization%20strategy%20d81c870ebc2d47d79cf22504c638457f/Untitled%201.png)

lalu pada menu manage role, tambahkan role dan atur perizinannya untuk role tersebut

![Untitled](role%20based%20autorization%20strategy%20d81c870ebc2d47d79cf22504c638457f/Untitled%202.png)

setelah itu, kita bisa assign role tersebut ke suatu user pada menu assign role

![Untitled](role%20based%20autorization%20strategy%20d81c870ebc2d47d79cf22504c638457f/Untitled%203.png)