# instalasi jenkins pada VPS ubuntu

## setup ssh

pada server kita, setup ssh menggunakan perintah

```bash
ssh-keygen
```

![Untitled](instalasi%20jenkins%20pada%20VPS%20ubuntu%20f03f077212494e0885c44a3ec40ca9c1/Untitled.png)

output pertama akan meminta lokasi dimana file ssh akan disimpan, input lokasi yang diinginkan. atau enter untuk membiarkan default
output kedua akan meminta passphrase, saya memilih untuk mengkosongkannya dengan menekan tombol enter

## instalasi jenkins

sebelum menginstall software, disarankan untuk melakukan update & upgrade (opsional) package menager, dengan menggunakan perintah

```bash
sudo apt update
sudo apt upgrade -y #opsional
```

![Untitled](instalasi%20jenkins%20pada%20VPS%20ubuntu%20f03f077212494e0885c44a3ec40ca9c1/Untitled%201.png)

setelah itu, instal git dan java 11 menggunakan perintah

```bash
sudo apt install git openjdk-11-jdk -y
```

![Untitled](instalasi%20jenkins%20pada%20VPS%20ubuntu%20f03f077212494e0885c44a3ec40ca9c1/Untitled%202.png)

kita akan menginstall jenkins versi 1.375.2 LTS menggunakan war file, download filenya terlebih dahulu menggunakan perintah

```bash
wget https://get.jenkins.io/war-stable/2.375.2/jenkins.war
```

![Untitled](instalasi%20jenkins%20pada%20VPS%20ubuntu%20f03f077212494e0885c44a3ec40ca9c1/Untitled%203.png)

jalankan jenkins menggunakan perintah

```bash
java -jar jenkins.war --httpPort=9090 &
```

![Untitled](instalasi%20jenkins%20pada%20VPS%20ubuntu%20f03f077212494e0885c44a3ec40ca9c1/Untitled%204.png)

setelah itu pada komputer lokal kita, buka browser lalu ketikan ip dan port jenkins

![Untitled](instalasi%20jenkins%20pada%20VPS%20ubuntu%20f03f077212494e0885c44a3ec40ca9c1/Untitled%205.png)

lalu untuk mengunlock jenkins, masukan kata sandi, kata sandi terdapat di direktori yang disebutkan jenkins

![Untitled](instalasi%20jenkins%20pada%20VPS%20ubuntu%20f03f077212494e0885c44a3ec40ca9c1/Untitled%206.png)

setelah itu kita diberi pilihan untuk install plugin yang direkomendasikan jenkins, atau kita dapat memilih sendiri plugin yang ingin di instal, ,pad

![Untitled](instalasi%20jenkins%20pada%20VPS%20ubuntu%20f03f077212494e0885c44a3ec40ca9c1/Untitled%207.png)

pada kasus pembelajaran kali ini, saya tidak akan menginstall plugin apapun karena saya akan menginstall plugin secara manual, jadi saya pilih select plugin to install > lalu saya pilih none supaya tidak menginstall plugin apapun

![Untitled](instalasi%20jenkins%20pada%20VPS%20ubuntu%20f03f077212494e0885c44a3ec40ca9c1/Untitled%208.png)

masukan form yang diperlukan

![Untitled](instalasi%20jenkins%20pada%20VPS%20ubuntu%20f03f077212494e0885c44a3ec40ca9c1/Untitled%209.png)

sesuaikan jenkins url

![Untitled](instalasi%20jenkins%20pada%20VPS%20ubuntu%20f03f077212494e0885c44a3ec40ca9c1/Untitled%2010.png)