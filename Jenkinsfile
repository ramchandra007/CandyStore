pipeline {
    agent any

    stages {
        stage('clone') {
            steps {
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/ramchandra007/CandyStore.git']]) 
            }
        }
        stage('docker') {
            steps {
                script {
                   withDockerRegistry(credentialsId: 'docker-cred') {
                         sh 'docker build -t ramchandramazzari/candystore .'
                         sh 'docker push ramchandramazzari/candystore'
                   }
               }
            }
        }
    }
}
