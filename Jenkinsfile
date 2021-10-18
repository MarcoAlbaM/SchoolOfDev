pipeline {
    agent any

    stages {
        stage('building') {
            steps {
                sh 'sudo docker build . -t minecraftserver'
                sh 'sudo docker image ls'
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
