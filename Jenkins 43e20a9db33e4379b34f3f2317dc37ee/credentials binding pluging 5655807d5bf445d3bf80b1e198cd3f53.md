# credentials binding pluging **

sebelumnya kita sudah menggunakan perintah credentials() untuk mengambil data dari Jenkins credentials secara aman

namun kita bisa menggunakan credentials hanya pada bagian tertentu, dan tidak mengeksposnya ke environment variable.

kita bisa menggunakan plugin credentials binding

```groovy
pipeline {
  agent none

    stages {
        withCredentials([usernamePassword(
            credentialsId: "reiya_rahasia"
            usernameVariable: "USER"
            passwordVariable; "PASSWORD"
        )]) {
            sh('echo "release it with -u $USER -p PASSWORD"')
        }
    }

}
```