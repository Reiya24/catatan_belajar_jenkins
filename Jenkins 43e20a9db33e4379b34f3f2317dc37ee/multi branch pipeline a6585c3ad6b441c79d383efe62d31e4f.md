# multi branch pipeline

jenkins pipeline memiliki fitur multi brach pipeline, dimana bisa secara otomatis mendeteksi branch yang terdapat di git. oleh karena itu jika terdapat branch baru, kita tidak perlu menambah job secara manual.

khusus multi branch pipeline, hanya bisa membuat pipeline dari Jenkinsfile, tidak bisa langsund di job nya

## membuat multi branch job

pada dashboard > new item > multibranch pipeline

![Untitled](multi%20branch%20pipeline%20a6585c3ad6b441c79d383efe62d31e4f/Untitled.png)

ssan multibranch pipeline trigger, untuk mengscan apakah ada branch baru

![Untitled](multi%20branch%20pipeline%20a6585c3ad6b441c79d383efe62d31e4f/Untitled%201.png)

tambahkan repository project

![Untitled](multi%20branch%20pipeline%20a6585c3ad6b441c79d383efe62d31e4f/Untitled%202.png)

jenkins akan mengscan repository kita

![Untitled](multi%20branch%20pipeline%20a6585c3ad6b441c79d383efe62d31e4f/Untitled%203.png)

![Untitled](multi%20branch%20pipeline%20a6585c3ad6b441c79d383efe62d31e4f/Untitled%204.png)

buat branch baru di github, jika ingin langsung mengscan branch baru, klik scan multibranch pipeline now

![Untitled](multi%20branch%20pipeline%20a6585c3ad6b441c79d383efe62d31e4f/Untitled%205.png)