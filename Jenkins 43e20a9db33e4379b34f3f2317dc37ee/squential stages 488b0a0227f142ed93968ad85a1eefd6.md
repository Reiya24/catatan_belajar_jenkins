# squential stages

stages bisa memiliki stage lagi di dalamnya, dan stage di dalamnya secara default akan dieksekusi secara sequential berurut

stages itu didalamnya hanya bisa memiliki satu perintah, misal steps, stages, pararel atau matrix

jadi jika kita tambahkan stages lagi, maka tidak bisa digabung dengan steps 

```groovy
pipeline {
    agent any

    stages {

        stage("testing") {

            stages {
                stage("testing hello world") {
                    steps {
                        echo("hello world")
                    }
                }

                stage("testing good bye world") {
                    steps {
                        echo("good bye world")
                    }
                }
            }
        }

    }
}
```

stage view

![Untitled](squential%20stages%20488b0a0227f142ed93968ad85a1eefd6/Untitled.png)

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
Checking out Revision 7e1852935914e44bc4a8637a4b3f08c2fa7153af (origin/main)
 > git config core.sparsecheckout # timeout=10
 > git checkout -f 7e1852935914e44bc4a8637a4b3f08c2fa7153af # timeout=10
Commit message: "Update Jenkinsfile"
 > git rev-list --no-walk 3d42ebb9dfdf3592818587a64b92a2a7c5adee9b # timeout=10
[Pipeline] }
[Pipeline] // stage
[Pipeline] withEnv
[Pipeline] {
[Pipeline] stage
[Pipeline] { (testing)
[Pipeline] stage
[Pipeline] { (testing hello world)
[Pipeline] echo
hello world
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (testing good bye world)
[Pipeline] echo
good bye world
[Pipeline] }
[Pipeline] // stage
[Pipeline] }
[Pipeline] // stage
[Pipeline] }
[Pipeline] // withEnv
[Pipeline] }
[Pipeline] // node
[Pipeline] End of Pipeline
Finished: SUCCESS
```