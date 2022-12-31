// Uses Declarative syntax to run commands inside a container.
pipeline {

    agent { 
        label 'centos7_Slave' 
    }

    triggers {
  pollSCM '* * * * *'
}
    stages {
        stage('checkout code') {
            steps {
                    checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'giladifrah', url: 'https://github.com/giladifrah/hello-world-war.git']])            }
        }
        stage('Build') {
            steps {
                sh "docker build -t war:$BUILD_ID ."
            }
        }
    }
}
