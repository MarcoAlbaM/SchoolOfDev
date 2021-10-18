pipeline {
    agent any

    stages {
        stage('Preparacion') {
            checkout scm
        }
        stage('Contruccion') {
            steps {
                sh 'cd SchoolOfDev'
            }
            steps {
                sh 'sudo docker build . -t minecraftserver:1'
            }
        }
        stage('Analisis') {
            steps {
                echo 'Deploying....'
            }
        }
        stage('Push') {
            steps {
                sh 'sudo docker push maamadmin/cicdassigment:1'
            }
        }
    }
}
