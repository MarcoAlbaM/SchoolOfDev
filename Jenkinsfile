pipeline {
    agent any

    stages {
        stage('building') {
            steps {
                sh 'docker build . -t minecraftserver'
                sh 'docker image ls'
            }
        }
        stage('Anal') {
            steps {
                echo 'Deploying....'
            }
        }
        stage('Push') {
            steps {
                echo 'Push...'
            }
        }
    }
}
