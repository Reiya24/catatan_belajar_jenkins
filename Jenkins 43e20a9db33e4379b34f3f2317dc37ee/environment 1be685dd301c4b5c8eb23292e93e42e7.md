# environment

pipeline mendukung penambahan environment variable.

jika environment variable ditambahkan di pipeline, maka semua stages bisa mendapatkan nilainya.

jika environment variable ditambahkan di stage, maka hanya bisa didapatkan di stage tersebut

## Contoh

Jenkinsfile

```bash
pipeline {
    agent any

    environment {
        AUTHOR = "Reiya Tenggara"
        USERNAME = "reiya24"
    }

    stages {

        stage("environment") {
            steps{
                echo("autor = ${AUTHOR}")
                echo("username = ${USERNAME}")
            }
        }

    }
}
```

stage view

![Untitled](environment%201be685dd301c4b5c8eb23292e93e42e7/Untitled.png)

console output

```bash
Started by user Reiya Tenggara
Obtained Jenkinsfile from git git@github.com:Reiya24/belajar-jenkins-pipeline.git
[Pipeline] Start of Pipeline
[Pipeline] node
Running on agent1 in /home/reiya24/jenkins_agent1/workspace/belajar pipeline
[Pipeline] {
[Pipeline] stage
[Pipeline] { (Declarative: Checkout SCM)
[Pipeline] checkout
Selected Git installation does not exist. Using Default
The recommended git tool is: NONE
using credential reiya24
Fetching changes from the remote Git repository
 > git rev-parse --resolve-git-dir /home/reiya24/jenkins_agent1/workspace/belajar pipeline/.git # timeout=10
 > git config remote.origin.url git@github.com:Reiya24/belajar-jenkins-pipeline.git # timeout=10
Fetching upstream changes from git@github.com:Reiya24/belajar-jenkins-pipeline.git
 > git --version # timeout=10
 > git --version # 'git version 2.34.1'
using GIT_SSH to set credentials 
Verifying host key using known hosts file, will automatically accept unseen keys
 > git fetch --tags --force --progress -- git@github.com:Reiya24/belajar-jenkins-pipeline.git +refs/heads/*:refs/remotes/origin/* # timeout=10
Checking out Revision 3d401325b1bd4ec391e7a8cd6df3c28a29b57ec5 (origin/main)
Commit message: "Update Jenkinsfile"
 > git rev-parse origin/main^{commit} # timeout=10
 > git config core.sparsecheckout # timeout=10
 > git checkout -f 3d401325b1bd4ec391e7a8cd6df3c28a29b57ec5 # timeout=10
 > git rev-list --no-walk 4947fbc95c1ca1f25650641546da0b6d9e11bb0f # timeout=10
[Pipeline] }
[Pipeline] // stage
[Pipeline] withEnv
[Pipeline] {
[Pipeline] withEnv
[Pipeline] {
[Pipeline] stage
[Pipeline] { (environment)
[Pipeline] echo
autor = Reiya Tenggara
[Pipeline] echo
username = reiya24
[Pipeline] }
[Pipeline] // stage
[Pipeline] }
[Pipeline] // withEnv
[Pipeline] }
[Pipeline] // withEnv
[Pipeline] }
[Pipeline] // node
[Pipeline] End of Pipeline
Finished: SUCCESS
```

## Credentials

di environment, terdapat perintah khusus bernama credentials(), yang bisa digunakan untuk mengambil data dari Jenkins Credentials. hal ini lebih aman dibandingkan harus diketik manual di Jenkinsfile. namun tidak semua jenis Credentials didukung, hanya beberapa saja yang bisa digunakan menggunakan perintah credentials()

## tipe Credentials yang bisa diambil

- Secret Text : secara otomatis environment variable berisi value dari secret text
- Secret File : secara otomatis environment variable berisi lokasi file secret yang secara temporary dibuat dan dihapus otomatis setelah pipeline selesai
- Username dan Password : secara otomatis environment variable berisi data username:password, dan secara otomatis akan dibuatkan environment variable dengan nama NAMA_USR dan NAMA_PSW
- SSH with private key : secara otomatis environment variable berisi lokasi file SSH yang secara temporary dibuat dan dihapus otomatis, dan juga secara otomatis akan dibuatkan environment variable NAMA_USR dan NAMA_PSW (berisi passphrase SSH)

## contoh

membuat credentials baru dengan bertipe username dan password (mengambil data dari environmet variable menggunakan ID)

![Untitled](environment%201be685dd301c4b5c8eb23292e93e42e7/Untitled%201.png)

Jenkinsfile

```bash
pipeline {
    agent any

    stages {

        stage("environment variable") {

            environment {
                APP = credentials("reiya_raasia")
            }

            steps{
                echo("username : ${APP_USR}")
                echo("password : ${APP_PSW}")
            }
        }

    }
}
```

stage view

![Untitled](environment%201be685dd301c4b5c8eb23292e93e42e7/Untitled%202.png)

![Untitled](environment%201be685dd301c4b5c8eb23292e93e42e7/Untitled%203.png)

terdapat warning karena menampilkan data yang tidak aman (password)

console output

```bash
Started by user Reiya Tenggara
Obtained Jenkinsfile from git git@github.com:Reiya24/belajar-jenkins-pipeline.git
[Pipeline] Start of Pipeline
[Pipeline] node
Running on agent1 in /home/reiya24/jenkins_agent1/workspace/belajar pipeline
[Pipeline] {
[Pipeline] stage
[Pipeline] { (Declarative: Checkout SCM)
[Pipeline] checkout
Selected Git installation does not exist. Using Default
The recommended git tool is: NONE
using credential reiya24
Fetching changes from the remote Git repository
 > git rev-parse --resolve-git-dir /home/reiya24/jenkins_agent1/workspace/belajar pipeline/.git # timeout=10
 > git config remote.origin.url git@github.com:Reiya24/belajar-jenkins-pipeline.git # timeout=10
Fetching upstream changes from git@github.com:Reiya24/belajar-jenkins-pipeline.git
 > git --version # timeout=10
 > git --version # 'git version 2.34.1'
using GIT_SSH to set credentials 
Verifying host key using known hosts file, will automatically accept unseen keys
 > git fetch --tags --force --progress -- git@github.com:Reiya24/belajar-jenkins-pipeline.git +refs/heads/*:refs/remotes/origin/* # timeout=10
Checking out Revision e797fa263d94dd9f7557a0cda9b547ff4e9fc3c8 (origin/main)
Commit message: "Update Jenkinsfile"
 > git rev-parse origin/main^{commit} # timeout=10
 > git config core.sparsecheckout # timeout=10
 > git checkout -f e797fa263d94dd9f7557a0cda9b547ff4e9fc3c8 # timeout=10
 > git rev-list --no-walk 41cbabcc1228a3d173628050bd9dc3aea073a663 # timeout=10
[Pipeline] }
[Pipeline] // stage
[Pipeline] withEnv
[Pipeline] {
[Pipeline] stage
[Pipeline] { (environment variable)
[Pipeline] withCredentials
Masking supported pattern matches of $APP or $APP_PSW
[Pipeline] {
[Pipeline] echo
username : reiya
[Pipeline] echo
Warning: A secret was passed to "echo" using Groovy String interpolation, which is insecure.
		 Affected argument(s) used the following variable(s): [APP_PSW]
		 See https://jenkins.io/redirect/groovy-string-interpolation for details.
password : ****
[Pipeline] }
[Pipeline] // withCredentials
[Pipeline] }
[Pipeline] // stage
[Pipeline] }
[Pipeline] // withEnv
[Pipeline] }
[Pipeline] // node
[Pipeline] End of Pipeline
Finished: SUCCESS
```

### sensitive information

perintah ${key} di dalam string interpolation seharusnya tidak digunakan untuk data sensitive, misal credentials.

agar informasi sensitive tidak terlihat, gunakan tanda ‘’ (petik satu), dan gunakan $KEY

### contoh

Jenkinsfile

```bash
pipeline {
    agent any

    stages {

        stage("environment variable") {

            environment {
                APP = credentials("reiya_rahasia")
            }

            steps{
                sh("echo 'password file rahasia: ${APP_PSW}' > 'rahasia.txt'")
                
                sh('echo "password fila secret.txt : $APP_PSW" > "secret.txt"')

            }
        }

    }
}
```

nilai dari environmet variable $APP_PSW akan dikirim ke file yang bernama rahasia.txt

perintah sh pertama akan menampilkan warning, perintah sh kedua tidak menampilkan warning, namun password tetap tidak terlihat

![Untitled](environment%201be685dd301c4b5c8eb23292e93e42e7/Untitled%204.png)

![Untitled](environment%201be685dd301c4b5c8eb23292e93e42e7/Untitled%205.png)

namun kita bisa melihat passwordnya di build history > workspace > klik link direktori 

dan passwornya ada di file yang bernama rahasia.txt dan secret.txt

![Untitled](environment%201be685dd301c4b5c8eb23292e93e42e7/Untitled%206.png)

![Untitled](environment%201be685dd301c4b5c8eb23292e93e42e7/Untitled%207.png)