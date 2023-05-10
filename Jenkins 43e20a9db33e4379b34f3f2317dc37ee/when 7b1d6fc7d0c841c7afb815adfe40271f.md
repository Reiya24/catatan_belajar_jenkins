# when

perintah yang digunakan untuk menentukan pada kondisi apa sebuah stage di eksekusi

when memiliki detail kondisi yang beragam [https://www.jenkins.io/doc/book/pipeline/syntax/#when](https://www.jenkins.io/doc/book/pipeline/syntax/#when)

## contoh

Jenkinsfile

```groovy
pipeline {
    agent any

    parameters {
        booleanParam(name: "DEPLOY", defaultValue: false, description: "need to deploy?")
    }

    stages {
        stage("test when") {

         when {
            expression {
                return params.DEPLOY;
            }
         }

            steps {
                echo("hello world")
            }      
        }
    }
}
```

ketika parameter DEPLOY tidak di ceklis, maka stage tersebut tidak akan dieksekusi

![Untitled](when%207b1d6fc7d0c841c7afb815adfe40271f/Untitled.png)

![Untitled](when%207b1d6fc7d0c841c7afb815adfe40271f/Untitled%201.png)

```groovy
Started by user Reiya Tenggara
Obtained Jenkinsfile from git git@github.com:Reiya24/belajar-jenkins-pipeline.git
[Pipeline] Start of Pipeline
[Pipeline] node
Running on Jenkins in /var/jenkins_home/workspace/belajar pipeline
[Pipeline] {
[Pipeline] stage
[Pipeline] { (Declarative: Checkout SCM)
[Pipeline] checkout
Selected Git installation does not exist. Using Default
The recommended git tool is: NONE
using credential reiya24
 > git rev-parse --resolve-git-dir /var/jenkins_home/workspace/belajar pipeline/.git # timeout=10
Fetching changes from the remote Git repository
 > git config remote.origin.url git@github.com:Reiya24/belajar-jenkins-pipeline.git # timeout=10
Fetching upstream changes from git@github.com:Reiya24/belajar-jenkins-pipeline.git
 > git --version # timeout=10
 > git --version # 'git version 2.30.2'
using GIT_SSH to set credentials 
Verifying host key using known hosts file, will automatically accept unseen keys
 > git fetch --tags --force --progress -- git@github.com:Reiya24/belajar-jenkins-pipeline.git +refs/heads/*:refs/remotes/origin/* # timeout=10
 > git rev-parse origin/main^{commit} # timeout=10
Checking out Revision 3d42ebb9dfdf3592818587a64b92a2a7c5adee9b (origin/main)
 > git config core.sparsecheckout # timeout=10
 > git checkout -f 3d42ebb9dfdf3592818587a64b92a2a7c5adee9b # timeout=10
Commit message: "Update Jenkinsfile"
 > git rev-list --no-walk 3d42ebb9dfdf3592818587a64b92a2a7c5adee9b # timeout=10
[Pipeline] }
[Pipeline] // stage
[Pipeline] withEnv
[Pipeline] {
[Pipeline] stage
[Pipeline] { (test when)
Stage "test when" skipped due to when conditional
[Pipeline] }
[Pipeline] // stage
[Pipeline] }
[Pipeline] // withEnv
[Pipeline] }
[Pipeline] // node
[Pipeline] End of Pipeline
Finished: SUCCESS
```

namun ketika parameter tersebut di ceklis, maka stage tersebut akan dijalankan

![Untitled](when%207b1d6fc7d0c841c7afb815adfe40271f/Untitled%202.png)

![Untitled](when%207b1d6fc7d0c841c7afb815adfe40271f/Untitled%203.png)

console output

```groovy
Started by user Reiya Tenggara
Obtained Jenkinsfile from git git@github.com:Reiya24/belajar-jenkins-pipeline.git
[Pipeline] Start of Pipeline
[Pipeline] node
Running on Jenkins in /var/jenkins_home/workspace/belajar pipeline
[Pipeline] {
[Pipeline] stage
[Pipeline] { (Declarative: Checkout SCM)
[Pipeline] checkout
Selected Git installation does not exist. Using Default
The recommended git tool is: NONE
using credential reiya24
 > git rev-parse --resolve-git-dir /var/jenkins_home/workspace/belajar pipeline/.git # timeout=10
Fetching changes from the remote Git repository
 > git config remote.origin.url git@github.com:Reiya24/belajar-jenkins-pipeline.git # timeout=10
Fetching upstream changes from git@github.com:Reiya24/belajar-jenkins-pipeline.git
 > git --version # timeout=10
 > git --version # 'git version 2.30.2'
using GIT_SSH to set credentials 
Verifying host key using known hosts file, will automatically accept unseen keys
 > git fetch --tags --force --progress -- git@github.com:Reiya24/belajar-jenkins-pipeline.git +refs/heads/*:refs/remotes/origin/* # timeout=10
 > git rev-parse origin/main^{commit} # timeout=10
Checking out Revision 3d42ebb9dfdf3592818587a64b92a2a7c5adee9b (origin/main)
 > git config core.sparsecheckout # timeout=10
 > git checkout -f 3d42ebb9dfdf3592818587a64b92a2a7c5adee9b # timeout=10
Commit message: "Update Jenkinsfile"
 > git rev-list --no-walk 3d42ebb9dfdf3592818587a64b92a2a7c5adee9b # timeout=10
[Pipeline] }
[Pipeline] // stage
[Pipeline] withEnv
[Pipeline] {
[Pipeline] stage
[Pipeline] { (test when)
[Pipeline] echo
hello world
[Pipeline] }
[Pipeline] // stage
[Pipeline] }
[Pipeline] // withEnv
[Pipeline] }
[Pipeline] // node
[Pipeline] End of Pipeline
Finished: SUCCESS
```