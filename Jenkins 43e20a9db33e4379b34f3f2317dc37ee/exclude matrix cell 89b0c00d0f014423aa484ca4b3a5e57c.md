# exclude matrix cell

matrix juga memiliki perintah exclude, jika kita ingin meng-exclude cell tertentu

misal pada kasus kita, ingin meng exclude mac 32

## contoh

```groovy
pipeline {
  agent none

      stages {

       stage("os setup") {
            matrix {
                axes {
                    axis {
                        name 'OS'
                        values 'linux', 'windows', 'mac'
                    }
                    axis {
                        name 'ARC'
                        values '32', '64'
                    }
                }
                excludes {
                    exclude {
                        axis {
                            name "OS"
                            values "mac"
                        }
                        axis {
                            name "ARC"
                            values "mac"
                        }
                    }
                }

                stages {
                    stage("echo") {
                        agent {
                            node {
                                label "22.04 && singapore"
                            }
                        }
                        steps {
                            echo("setup ${OS} ${ARC}")
                        }
                    }
                }
            }
        }
    }
}
```

stage view

![Untitled](exclude%20matrix%20cell%2089b0c00d0f014423aa484ca4b3a5e57c/Untitled.png)

console output

```groovy
Started by user Reiya Tenggara
Obtained Jenkinsfile from git git@github.com:Reiya24/belajar-jenkins-pipeline.git
[Pipeline] Start of Pipeline
[Pipeline] stage
[Pipeline] { (os setup)
[Pipeline] parallel
[Pipeline] { (Branch: Matrix - OS = 'linux', ARC = '32')
[Pipeline] { (Branch: Matrix - OS = 'windows', ARC = '32')
[Pipeline] { (Branch: Matrix - OS = 'mac', ARC = '32')
[Pipeline] { (Branch: Matrix - OS = 'linux', ARC = '64')
[Pipeline] { (Branch: Matrix - OS = 'windows', ARC = '64')
[Pipeline] { (Branch: Matrix - OS = 'mac', ARC = '64')
[Pipeline] stage
[Pipeline] { (Matrix - OS = 'linux', ARC = '32')
[Pipeline] stage
[Pipeline] { (Matrix - OS = 'windows', ARC = '32')
[Pipeline] stage
[Pipeline] { (Matrix - OS = 'mac', ARC = '32')
[Pipeline] stage
[Pipeline] { (Matrix - OS = 'linux', ARC = '64')
[Pipeline] stage
[Pipeline] { (Matrix - OS = 'windows', ARC = '64')
[Pipeline] stage
[Pipeline] { (Matrix - OS = 'mac', ARC = '64')
[Pipeline] withEnv
[Pipeline] {
[Pipeline] withEnv
[Pipeline] {
[Pipeline] withEnv
[Pipeline] {
[Pipeline] withEnv
[Pipeline] {
[Pipeline] withEnv
[Pipeline] {
[Pipeline] withEnv
[Pipeline] {
[Pipeline] stage
[Pipeline] { (echo)
[Pipeline] stage
[Pipeline] { (echo)
[Pipeline] stage
[Pipeline] { (echo)
[Pipeline] stage
[Pipeline] { (echo)
[Pipeline] stage
[Pipeline] { (echo)
[Pipeline] stage
[Pipeline] { (echo)
[Pipeline] node
Running on agent1 in /home/reiya24/jenkins_agent1/workspace/belajar pipeline
[Pipeline] node
[Pipeline] node
[Pipeline] node
[Pipeline] node
[Pipeline] node
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
Checking out Revision 2effa5c764a52a706132d192764efd1df7ac4c55 (origin/main)
Commit message: "Update Jenkinsfile"
 > git rev-parse origin/main^{commit} # timeout=10
 > git config core.sparsecheckout # timeout=10
 > git checkout -f 2effa5c764a52a706132d192764efd1df7ac4c55 # timeout=10
 > git rev-list --no-walk c557303de51ce6acf1e8d7566a0811d2f3a656a8 # timeout=10
[Pipeline] withEnv
[Pipeline] {
[Pipeline] echo
setup linux 32
[Pipeline] }
[Pipeline] // withEnv
[Pipeline] }
Running on agent1 in /home/reiya24/jenkins_agent1/workspace/belajar pipeline
[Pipeline] // node
[Pipeline] }
[Pipeline] {
[Pipeline] // stage
[Pipeline] }
[Pipeline] // withEnv
[Pipeline] }
[Pipeline] // stage
[Pipeline] }
[Pipeline] checkout
Selected Git installation does not exist. Using Default
The recommended git tool is: NONE
using credential reiya24
Still waiting to schedule task
Waiting for next available executor on ‘agent1’
Still waiting to schedule task
Waiting for next available executor on ‘agent1’
Still waiting to schedule task
Waiting for next available executor on ‘agent1’
Still waiting to schedule task
Waiting for next available executor on ‘agent1’
Fetching changes from the remote Git repository
 > git rev-parse --resolve-git-dir /home/reiya24/jenkins_agent1/workspace/belajar pipeline/.git # timeout=10
 > git config remote.origin.url git@github.com:Reiya24/belajar-jenkins-pipeline.git # timeout=10
Fetching upstream changes from git@github.com:Reiya24/belajar-jenkins-pipeline.git
 > git --version # timeout=10
 > git --version # 'git version 2.34.1'
using GIT_SSH to set credentials 
Verifying host key using known hosts file, will automatically accept unseen keys
 > git fetch --tags --force --progress -- git@github.com:Reiya24/belajar-jenkins-pipeline.git +refs/heads/*:refs/remotes/origin/* # timeout=10
Checking out Revision 2effa5c764a52a706132d192764efd1df7ac4c55 (origin/main)
Commit message: "Update Jenkinsfile"
[Pipeline] withEnv
[Pipeline] {
[Pipeline] echo
setup windows 32
[Pipeline] }
 > git rev-parse origin/main^{commit} # timeout=10
 > git config core.sparsecheckout # timeout=10
 > git checkout -f 2effa5c764a52a706132d192764efd1df7ac4c55 # timeout=10
[Pipeline] // withEnv
[Pipeline] }
Running on agent1 in /home/reiya24/jenkins_agent1/workspace/belajar pipeline
[Pipeline] // node
[Pipeline] }
[Pipeline] {
[Pipeline] // stage
[Pipeline] }
[Pipeline] // withEnv
[Pipeline] }
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
Checking out Revision 2effa5c764a52a706132d192764efd1df7ac4c55 (origin/main)
Commit message: "Update Jenkinsfile"
 > git rev-parse origin/main^{commit} # timeout=10
 > git config core.sparsecheckout # timeout=10
 > git checkout -f 2effa5c764a52a706132d192764efd1df7ac4c55 # timeout=10
[Pipeline] withEnv
[Pipeline] {
[Pipeline] echo
setup mac 32
[Pipeline] }
[Pipeline] // withEnv
[Pipeline] }
Running on agent1 in /home/reiya24/jenkins_agent1/workspace/belajar pipeline
[Pipeline] // node
[Pipeline] }
[Pipeline] {
[Pipeline] // stage
[Pipeline] }
[Pipeline] // withEnv
[Pipeline] }
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
Checking out Revision 2effa5c764a52a706132d192764efd1df7ac4c55 (origin/main)
Commit message: "Update Jenkinsfile"
[Pipeline] withEnv
[Pipeline] {
 > git rev-parse origin/main^{commit} # timeout=10
 > git config core.sparsecheckout # timeout=10
 > git checkout -f 2effa5c764a52a706132d192764efd1df7ac4c55 # timeout=10
[Pipeline] echo
setup linux 64
[Pipeline] }
[Pipeline] // withEnv
[Pipeline] }
Running on agent1 in /home/reiya24/jenkins_agent1/workspace/belajar pipeline
[Pipeline] // node
[Pipeline] }
[Pipeline] {
[Pipeline] // stage
[Pipeline] }
[Pipeline] // withEnv
[Pipeline] }
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
Checking out Revision 2effa5c764a52a706132d192764efd1df7ac4c55 (origin/main)
Commit message: "Update Jenkinsfile"
 > git rev-parse origin/main^{commit} # timeout=10
 > git config core.sparsecheckout # timeout=10
 > git checkout -f 2effa5c764a52a706132d192764efd1df7ac4c55 # timeout=10
[Pipeline] withEnv
[Pipeline] {
[Pipeline] echo
setup windows 64
[Pipeline] }
[Pipeline] // withEnv
[Pipeline] }
Running on agent1 in /home/reiya24/jenkins_agent1/workspace/belajar pipeline
[Pipeline] // node
[Pipeline] }
[Pipeline] {
[Pipeline] // stage
[Pipeline] }
[Pipeline] // withEnv
[Pipeline] }
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
Checking out Revision 2effa5c764a52a706132d192764efd1df7ac4c55 (origin/main)
Commit message: "Update Jenkinsfile"
[Pipeline] withEnv
[Pipeline] {
[Pipeline] echo
setup mac 64
[Pipeline] }
[Pipeline] // withEnv
 > git rev-parse origin/main^{commit} # timeout=10
 > git config core.sparsecheckout # timeout=10
 > git checkout -f 2effa5c764a52a706132d192764efd1df7ac4c55 # timeout=10
[Pipeline] }
[Pipeline] // node
[Pipeline] }
[Pipeline] // stage
[Pipeline] }
[Pipeline] // withEnv
[Pipeline] }
[Pipeline] // stage
[Pipeline] }
[Pipeline] // parallel
[Pipeline] }
[Pipeline] // stage
[Pipeline] End of Pipeline
Finished: SUCCESS
```