pipeline {
    agent any

    stages {
        stage('Build app') {
            steps {
                checkout scmGit(
                    branches: [[name: '*/main']],
                    extensions: [],
                    userRemoteConfigs: [[url: 'https://github.com/PrajwalAghor/Ise3.git']]
                )
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    bat 'docker build -t jenkinsdocker .'
                }
            }
        }

        stage('Rename Image Tag') {
            steps {
                script {
                    bat 'docker tag jenkinsdocker prajwalaghor01/jenkinsdockerapp:image'
                }
            }
        }

        stage('Push Image to docker Hub') {
            steps {
                script {
                    bat 'docker login -u prajwalaghor01 -p Prajwal#264'
                    bat 'docker push prajwalagho01/jenkinsdockerapp:image'
                }
            }
        }
    }
}


