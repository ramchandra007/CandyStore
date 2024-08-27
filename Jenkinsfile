pipeline {
    agent any

    stages {
        stage('clone') {
            steps {
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/smuralimohan123/CandyStore.git']]) 
            }
        }
        stage('docker') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-cred1') {
                         sh 'docker build -t svnmuralimohan/candystore .'
                         sh 'docker push svnmuralimohan/candystore:latest'
                   }
               }
            }
        }
    }
}
