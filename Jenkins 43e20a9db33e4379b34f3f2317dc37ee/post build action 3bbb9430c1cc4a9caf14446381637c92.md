# post build action

fitur ini biasanya digunakan untuk memberitahu status sebuah job ketika proses build selesai, misal, setelah sebuah job selesai, kita ingin mengirim statusnya ke email, chat atau yang lainnya, contohnya mengirim status job ke slack, salah satu platform untuk chat yang lumayan populer di dunia kerja

## mengirim status job ke slack

install plugin slack notification, jika mengalami eror 403, baca halaman dibawah

[troubleshooting **HTTP ERROR 403 No valid crumb was included in the request**](troubleshooting%20HTTP%20ERROR%20403%20No%20valid%20crumb%20was%20%203cbda28aed0149158464c824d9be9ff5.md)

## setup slack jenkins integration

buka halaman [https://my.slack.com/services/new/jenkins-ci](https://my.slack.com/services/new/jenkins-ci), lalu pilih workspace

![Untitled](post%20build%20action%203bbb9430c1cc4a9caf14446381637c92/Untitled.png)

pilih channel yang akan digunakan

![Untitled](post%20build%20action%203bbb9430c1cc4a9caf14446381637c92/Untitled%201.png)

setelah itu scroll kebawah, kita akan menemukan team subdomain, dan integration token credential ID

![Untitled](post%20build%20action%203bbb9430c1cc4a9caf14446381637c92/Untitled%202.png)

 copy integration token credential ID, lalu tambahkan di credential jenkins, pada menu kind, pilih secret text

![Untitled](post%20build%20action%203bbb9430c1cc4a9caf14446381637c92/Untitled%203.png)

setelah itu, pada dashboard jenkins > manage jenkins > configure system, cari menu slack, masukan form yang diperlukan, untuk workspace masukan team subdomain tadi, disarankan untuk test connection terlebih dahulu sebelum save

![Untitled](post%20build%20action%203bbb9430c1cc4a9caf14446381637c92/Untitled%204.png)

setelah itu, jika kita ingin mengirim notifikasi ke suatu job, masuk ke job tersebut > configure > post build action > slack notification, lalu pilih jenis notifikasi apa yang akan dikirim, kita bisa klik menu advanced untuk melihat pengaturan lanjutan

![Untitled](post%20build%20action%203bbb9430c1cc4a9caf14446381637c92/Untitled%205.png)

sekarang bila kita melakukan build, jenkins akan mengirimkan notifikasi ke slack

![Untitled](post%20build%20action%203bbb9430c1cc4a9caf14446381637c92/Untitled%206.png)