# trigger build remotely

jenkins memiliki fitur dimana kita bisa meminta jenkins untuk menjalankan job secara remote.

untuk melakukan itu, pada setelan konfigurasi job kita, ceklis trigger builds remotely, lalu buat token autentikasi

![Untitled](trigger%20build%20remotely%20b1d526be52914201815df1168f3fdfda/Untitled.png)

untuk melakukan build secara remote kita cukup akses halaman web / curl JENKINS_URL/job/belajar%20build%20remote/build?token=TOKEN_NAME

![Untitled](trigger%20build%20remotely%20b1d526be52914201815df1168f3fdfda/Untitled%201.png)

maka jenkins akan melakukan build secara otomatis

![Untitled](trigger%20build%20remotely%20b1d526be52914201815df1168f3fdfda/Untitled%202.png)