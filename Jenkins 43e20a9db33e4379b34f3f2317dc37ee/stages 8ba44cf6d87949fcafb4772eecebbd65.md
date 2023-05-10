# stages

bagian dimana terdapat satu atau lebih stage, stage biasanya berisikan detail dari tahapan dalam contiunous delivery yang kita buat di pipeline.

tidak ada aturan cara penamaan stage.

contoh penggunaan stage contohnya adalah build, test deploy, dan lain lain

stage akan dijalankan secara sequential berurut, jika pada stage terdapat error, maka stage selanjutanya tidak akan dieksekusi 

## stage example

Jenkinsfile

```bash
pipeline {
    agent {
        node {
            label "22.04 && singapore"
        }
    }

    stages {
        
        stage("build") {
            steps {
                echo("build")
            }
        }

        stage("test"){
            steps {
                echo("test")
            }
        }

        stage("deploy"){
            steps {
                echo("deploy")
            }
        }

    }

}
```

stage view:

![Untitled](stages%208ba44cf6d87949fcafb4772eecebbd65/Untitled.png)

console output:

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
 > git rev-parse origin/main^{commit} # timeout=10
Checking out Revision 016823449329b9922aa50e1d25e1c7f3157c248e (origin/main)
Commit message: "Update Jenkinsfile"
 > git config core.sparsecheckout # timeout=10
 > git checkout -f 016823449329b9922aa50e1d25e1c7f3157c248e # timeout=10
 > git rev-list --no-walk ea4a6de85d9211717bb33f12389c5461b71f07d8 # timeout=10
[Pipeline] }
[Pipeline] // stage
[Pipeline] withEnv
[Pipeline] {
[Pipeline] stage
[Pipeline] { (build)
[Pipeline] echo
build
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (test)
[Pipeline] echo
test
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (deploy)
[Pipeline] echo
deploy
[Pipeline] }
[Pipeline] // stage
[Pipeline] }
[Pipeline] // withEnv
[Pipeline] }
[Pipeline] // node
[Pipeline] End of Pipeline
Finished: SUCCESS
```