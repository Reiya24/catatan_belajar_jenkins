# utility steps

plugin yang berisikan utility yang bisa digunakan untuk mempermudah pembuatan pipeline, contoh: membaca file, membuat archive file, ,membuat hash, dan lain-lain

secara default, plugin ini tidak tersedia di jenkins, jadi kita harus menginstallnya secara manual

![Untitled](utility%20steps%2070d1e7a4c6e84b8995b8140f1e0dc3cd/Untitled.png)

dokumentasi penggunaan utility step dapat dilihat disini [https://www.jenkins.io/doc/pipeline/steps/pipeline-utility-steps/](https://www.jenkins.io/doc/pipeline/steps/pipeline-utility-steps/)

## contoh penggunaan utilty step

Jenkinsfile. menggunakan perintah writeJSON untuk menulis data json yang berisi dictionary groovy

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
                    def data = [
                        "firstName": "tomkun",
                        "lastName": "miki"
                    ]
                    writeJSON(file: 'data.json', json: data)
                }
            }
        }
    }
}
```

stage view

![Untitled](utility%20steps%2070d1e7a4c6e84b8995b8140f1e0dc3cd/Untitled%201.png)

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
Checking out Revision 8b7d02d3b741131b66a7051d042387d4c1c7f681 (origin/main)
Commit message: "Update Jenkinsfile"
 > git rev-parse origin/main^{commit} # timeout=10
 > git config core.sparsecheckout # timeout=10
 > git checkout -f 8b7d02d3b741131b66a7051d042387d4c1c7f681 # timeout=10
 > git rev-list --no-walk 7d3675248ae2bf968793309c5cd7a3c64183037c # timeout=10
[Pipeline] }
[Pipeline] // stage
[Pipeline] withEnv
[Pipeline] {
[Pipeline] stage
[Pipeline] { (script groovy)
[Pipeline] script
[Pipeline] {
[Pipeline] writeJSON
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

pada history build, pilih workspace

![Untitled](utility%20steps%2070d1e7a4c6e84b8995b8140f1e0dc3cd/Untitled%202.png)

klik alamat direktori

![Untitled](utility%20steps%2070d1e7a4c6e84b8995b8140f1e0dc3cd/Untitled%203.png)

akan ada file data.json

![Untitled](utility%20steps%2070d1e7a4c6e84b8995b8140f1e0dc3cd/Untitled%204.png)

![Untitled](utility%20steps%2070d1e7a4c6e84b8995b8140f1e0dc3cd/Untitled%205.png)