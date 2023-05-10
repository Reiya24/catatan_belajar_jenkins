# agent per stage

saat kita menggunakan agent, secara otomatis semua stage akan jalan di agent tersebut, tapi kita bisa menjalankan menggunakan agent yang berbeda di setiap stage. dengan cara jadikan agent di pipeline menjadi none, lalu tambahkan agent di tiap stage

## contoh

Jenkinsfile

```bash
pipeline {
    agent none

    stages {

        stage("stage di node1") {
            //agent
            agent{
                node{
                    label "22.04 && singapore"
                }
            }

            //steps
            steps{

                echo("hello from node1")
            }
        }

        stage("stage di master") {
            agent none

            steps{
                echo("hello from master")
            }
        }

    }
}
```

stage view

![Untitled](agent%20per%20stage%2079fb421477f845908a80c9faed10a567/Untitled.png)

console output

```bash
Started by user Reiya Tenggara
Obtained Jenkinsfile from git git@github.com:Reiya24/belajar-jenkins-pipeline.git
[Pipeline] Start of Pipeline
[Pipeline] stage
[Pipeline] { (stage di node1)
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
Checking out Revision c5bd913b907d84830959c100e8ae796861f669cc (origin/main)
Commit message: "Update Jenkinsfile"
 > git rev-parse origin/main^{commit} # timeout=10
 > git config core.sparsecheckout # timeout=10
 > git checkout -f c5bd913b907d84830959c100e8ae796861f669cc # timeout=10
 > git rev-list --no-walk c5bd913b907d84830959c100e8ae796861f669cc # timeout=10
[Pipeline] withEnv
[Pipeline] {
[Pipeline] echo
hello from node1
[Pipeline] }
[Pipeline] // withEnv
[Pipeline] }
[Pipeline] // node
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (stage di master)
[Pipeline] echo
hello from master
[Pipeline] }
[Pipeline] // stage
[Pipeline] End of Pipeline
Finished: SUCCESS
```