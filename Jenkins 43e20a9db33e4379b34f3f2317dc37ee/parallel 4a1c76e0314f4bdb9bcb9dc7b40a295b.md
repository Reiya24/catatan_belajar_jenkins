# parallel

secara default parallel akan menunggu semua proses selesai, walaupun ada salah satu stage yang error

namun jika kita ingin otomatis menghentikan semua proses stage ketika ada error di salah satu stage, kita bisa menambahkan perintah failFast, atau menambahkan parallelAlwaysFailFast() id option

saat menggunakan parallel, kita tidak bisa menambahkan agent di stage atasnya, oleh karena itu kita perlu tentukan di tiap stage prallelnya

## contoh

```groovy
pipeline {
  agent none

  stages {

    stage("testing") {
      parallel {
        stage("test hello world") {
          agent {
            node {
              label "22.04 && singapore"
            }
          }
          steps {
            echo("hello world")
            sleep(5)
          }
        }
        stage("test goodbye world") {
          agent {
            node {
              label "22.04 && singapore"
            }
          }
          steps {
            echo("goodbye world")
            sleep(5)
          }
        }
      }
    }
  }
}
```

stage view

![Untitled](parallel%204a1c76e0314f4bdb9bcb9dc7b40a295b/Untitled.png)

console output

```groovy
Started by user Reiya Tenggara
Replayed #91
[Pipeline] Start of Pipeline
[Pipeline] stage
[Pipeline] { (testing)
[Pipeline] parallel
[Pipeline] { (Branch: test hello world)
[Pipeline] { (Branch: test goodbye world)
[Pipeline] stage
[Pipeline] { (test hello world)
[Pipeline] stage
[Pipeline] { (test goodbye world)
[Pipeline] node
[Pipeline] node
Running on agent1 in /home/reiya24/jenkins_agent1/workspace/belajar pipeline
[Pipeline] {
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
Checking out Revision 4923b53cb215861ba6ffc852233e4e83b0706088 (origin/main)
Commit message: "Update Jenkinsfile"
 > git rev-parse origin/main^{commit} # timeout=10
 > git config core.sparsecheckout # timeout=10
 > git checkout -f 4923b53cb215861ba6ffc852233e4e83b0706088 # timeout=10
 > git rev-list --no-walk 4923b53cb215861ba6ffc852233e4e83b0706088 # timeout=10
[Pipeline] withEnv
[Pipeline] {
[Pipeline] echo
hello world
[Pipeline] sleep
Sleeping for 5 sec
Still waiting to schedule task
Waiting for next available executor on ‘agent1’
[Pipeline] }
[Pipeline] // withEnv
[Pipeline] }
Running on agent1 in /home/reiya24/jenkins_agent1/workspace/belajar pipeline
[Pipeline] // node
[Pipeline] }
[Pipeline] {
[Pipeline] // stage
[Pipeline] }
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
Checking out Revision 4923b53cb215861ba6ffc852233e4e83b0706088 (origin/main)
Commit message: "Update Jenkinsfile"
[Pipeline] withEnv
[Pipeline] {
[Pipeline] echo
goodbye world
[Pipeline] sleep
Sleeping for 5 sec
 > git rev-parse origin/main^{commit} # timeout=10
 > git config core.sparsecheckout # timeout=10
 > git checkout -f 4923b53cb215861ba6ffc852233e4e83b0706088 # timeout=10
[Pipeline] }
[Pipeline] // withEnv
[Pipeline] }
[Pipeline] // node
[Pipeline] }
[Pipeline] // stage
[Pipeline] }
[Pipeline] // parallel
[Pipeline] }
[Pipeline] // stage
[Pipeline] End of Pipeline
Finished: SUCCESS
```