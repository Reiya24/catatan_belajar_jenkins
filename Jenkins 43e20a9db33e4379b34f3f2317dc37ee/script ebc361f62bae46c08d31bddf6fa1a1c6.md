# script

pipeline mendukung script, agar kita bisa menyisipkan kode groovy pada pipeline menggunakan tag script.

dokumentasi bahasa pemrograman groovy dapat dilihat disini : [https://groovy-lang.org/](https://groovy-lang.org/)

## contoh:

Jenkinsfile

```bash
pipeline {
    agent {
        node {
            label '22.04 && singapore'
        }
    }

    stages {
        stage('script groovy') {
            steps{
                script {
                    for (int i = 0; i < 10; i++) {
                     echo("perulangan ke ${i}")
                    }
                }
            }
        }
    }
}
```

stage view

![Untitled](script%20ebc361f62bae46c08d31bddf6fa1a1c6/Untitled.png)

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
Checking out Revision 7d3675248ae2bf968793309c5cd7a3c64183037c (origin/main)
Commit message: "Update Jenkinsfile"
 > git rev-parse origin/main^{commit} # timeout=10
 > git config core.sparsecheckout # timeout=10
 > git checkout -f 7d3675248ae2bf968793309c5cd7a3c64183037c # timeout=10
 > git rev-list --no-walk 0c2fe82ca03447a0b1e701ab7a9f55c17470fdce # timeout=10
[Pipeline] }
[Pipeline] // stage
[Pipeline] withEnv
[Pipeline] {
[Pipeline] stage
[Pipeline] { (script groovy)
[Pipeline] script
[Pipeline] {
[Pipeline] echo
perulangan ke 0
[Pipeline] echo
perulangan ke 1
[Pipeline] echo
perulangan ke 2
[Pipeline] echo
perulangan ke 3
[Pipeline] echo
perulangan ke 4
[Pipeline] echo
perulangan ke 5
[Pipeline] echo
perulangan ke 6
[Pipeline] echo
perulangan ke 7
[Pipeline] echo
perulangan ke 8
[Pipeline] echo
perulangan ke 9
[Pipeline] }
[Pipeline] // script
[Pipeline] }
[Pipeline] // stage
[Pipeline] }
[Pipeline] // withEnv
[Pipeline] }
[Pipeline] // node
[Pipeline] End of Pipeline
Finished: SUCCESS
```