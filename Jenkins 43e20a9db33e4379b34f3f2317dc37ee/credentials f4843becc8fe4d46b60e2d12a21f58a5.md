# credentials

saat kita melakukan koneksi ke git, biasanya kita perlu credential SSH, Jenkins bisa menggunakan bawaan dari sistem operasinya, namun hal ini tidak disarankan, karena kedepannya ketika kita setup beberapa server untuk jenkins, kemungkinan credential SSH nya bisa berbeda, oleh karena itu, baiknya semua informasi credential disimpan di jenkins.

Jenkins memiliki fitur credentials untuk menyimpan credential kita, salah satunya adalah ccredential untuk SSH

## setup credentials

copy private key server kita di server, lalu paste ke credentials jenkins

pilih manage jenkins

![Untitled](credentials%20f4843becc8fe4d46b60e2d12a21f58a5/Untitled.png)

manage credentials

![Untitled](credentials%20f4843becc8fe4d46b60e2d12a21f58a5/Untitled%201.png)

klik (global)

![Untitled](credentials%20f4843becc8fe4d46b60e2d12a21f58a5/Untitled%202.png)

add credentials

![Untitled](credentials%20f4843becc8fe4d46b60e2d12a21f58a5/Untitled%203.png)

isi form

![Untitled](credentials%20f4843becc8fe4d46b60e2d12a21f58a5/Untitled%204.png)

![Untitled](credentials%20f4843becc8fe4d46b60e2d12a21f58a5/Untitled%205.png)