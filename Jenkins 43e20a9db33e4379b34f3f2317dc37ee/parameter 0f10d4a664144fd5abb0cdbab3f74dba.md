# parameter

kita bisa menambahkan parameter di pipeline, dengan cara menggunakan perintah parameters. parameter yang diinputkan oleh user akan secara otomatis disimpan dalam global variable

## parameter type

- string, untuk tipe parameter string / text
- text, mirip seperti string, namun input akan berupa multiline text area
- booleanParam, untuk tipe parameter boolean (true/false)
- choice, untuk tipe parameter string / text dengan opsi pilihan yang sudah disediakan
- password, untuk tipe parameter string yang dianggap sensitif

## contoh parameter

```bash
pipeline {
    agent any

    parameters{
        string(name: "NAME", defaultValue: "guest", description : "what is your name?")
        text(name: "DESCRIPTION", defaultValue: "guest", description: "tell me about you")
        booleanParam(name: "DEPLOY", defaultValue: false, description: "need to deploy")
        choice(name: "SOCIAL_MEDIA", choices: ['instagram', 'facebook', 'twitter'], description: "which social media?")
        password(name: "SECRET", defaultValue: "", description: "encrypt key")
    }

    stages {
        stage("test parameter") {
            steps {
                echo("hello ${params.NAME}")
                echo("your description is ${params.DESCRIPTION}")
                echo("your social media is ${params.SOCIALMEDIA}")
                echo("need to deploy ${params.DEPLOY} to deploy")
                echo("your secret is ${params.SECRET}")
            }
        }
    }
}
```

sekarang berubah menjadi build with parameter

![Untitled](parameter%200f10d4a664144fd5abb0cdbab3f74dba/Untitled.png)

stage view

![Untitled](parameter%200f10d4a664144fd5abb0cdbab3f74dba/Untitled%201.png)

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
Checking out Revision 5f2a7b6e2c682005941744c1c71424f68f7c3e3c (origin/main)
Commit message: "Update Jenkinsfile"
 > git rev-parse origin/main^{commit} # timeout=10
 > git config core.sparsecheckout # timeout=10
 > git checkout -f 5f2a7b6e2c682005941744c1c71424f68f7c3e3c # timeout=10
 > git rev-list --no-walk 5f2a7b6e2c682005941744c1c71424f68f7c3e3c # timeout=10
[Pipeline] }
[Pipeline] // stage
[Pipeline] withEnv
[Pipeline] {
[Pipeline] stage
[Pipeline] { (test parameter)
[Pipeline] echo
hello reiya
[Pipeline] echo
your description is meong
[Pipeline] echo
your social media is null
[Pipeline] echo
need to deploy true to deploy
[Pipeline] echo
your secret is 
[Pipeline] }
[Pipeline] // stage
[Pipeline] }
[Pipeline] // withEnv
[Pipeline] }
[Pipeline] // node
[Pipeline] End of Pipeline
Finished: SUCCESS
```