# integrasi dengan git

pastikan memiliki project di github yang bisa digunakan sebagai sumber kode untuk jenkins job yang sudah kita buat

pada server kita, masukan dibawah agar github dapat memberi akses

```bash
ssh-keyscan -H github.com >> ~/.ssh/known_hosts
```

pada job yang sudah dibuat, klik configure > source management > klik checkbox git > masukan repository URL, credentials, branch yang akan di build

![Untitled](integrasi%20dengan%20git%2035317e63bb5b40deb306226cd4c95e01/Untitled.png)

untuk melakukan proses build, kita bisa mengklik build now

![Untitled](integrasi%20dengan%20git%2035317e63bb5b40deb306226cd4c95e01/Untitled%201.png)

jika build berhasil, pada menu workspace kita bisa melihat project github kita

![Untitled](integrasi%20dengan%20git%2035317e63bb5b40deb306226cd4c95e01/Untitled%202.png)

kita dapat melihat detail build dengan mengklik hasil build

![Untitled](integrasi%20dengan%20git%2035317e63bb5b40deb306226cd4c95e01/Untitled%203.png)

![Untitled](integrasi%20dengan%20git%2035317e63bb5b40deb306226cd4c95e01/Untitled%204.png)