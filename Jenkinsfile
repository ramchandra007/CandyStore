pipeline {
    agent any

    stages {
        stage('clone') {
            steps {
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Praveenchinna14/CandyStore.git']]) 
            }
        }
        stage('docker') {
            steps {
                script {
                     withDockerRegistry(credentialsId: 'docker-cred1') {
                         sh 'docker build -t praveenchinna/candystore .'
                         sh 'docker push praveenchinna/candystore:latest'
                   }
               }
            }
        }
    }
}
