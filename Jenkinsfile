pipeline {
    agent any

    stages {
        stage('Preparacion') {
            steps {
                sh 'git clone https://github.com/MarcoAlbaM/SchoolOfDev.git'
            }
        }
        stage('Contruccion') {
            steps {
                sh 'sudo docker build 
            }
        }
        stage('Analisis') {
            steps {
                echo 'Deploying....'
            }
        }
        stage('Push') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
