# basic steps

selain perintah echo, masih banyak perintah lainnya, kita bisa melihat daftar perintah yang tersedia pada link berikut

[https://www.jenkins.io/doc/pipeline/steps/workflow-basic-steps/](https://www.jenkins.io/doc/pipeline/steps/workflow-basic-steps/)

## contoh basic step

Jenkinsfile:

menambahkan perintah sleep selama 5 detik

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
                echo("build 1")
                sleep(5)
                echo("build 2")
                sleep(5)
                echo("build 3")
            }
        }
    }
}
```

hasil console output :

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
Checking out Revision 5ba4f86ab376abbbf6f5a68c58068712b56df65c (origin/main)
Commit message: "Update Jenkinsfile"
 > git rev-parse origin/main^{commit} # timeout=10
 > git config core.sparsecheckout # timeout=10
 > git checkout -f 5ba4f86ab376abbbf6f5a68c58068712b56df65c # timeout=10
 > git rev-list --no-walk 5ba4f86ab376abbbf6f5a68c58068712b56df65c # timeout=10
[Pipeline] }
[Pipeline] // stage
[Pipeline] withEnv
[Pipeline] {
[Pipeline] stage
[Pipeline] { (build)
[Pipeline] echo
build 1
[Pipeline] sleep
Sleeping for 5 sec
[Pipeline] echo
build 2
[Pipeline] sleep
Sleeping for 5 sec
[Pipeline] echo
build 3
[Pipeline] }
[Pipeline] // stage
[Pipeline] }
[Pipeline] // withEnv
[Pipeline] }
[Pipeline] // node
[Pipeline] End of Pipeline
Finished: SUCCESS
```