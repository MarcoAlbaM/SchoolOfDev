pipeline {
    agent any

    stages {
        stage('checkout') {
            steps {
                checkout scm
            }  
        }
        stage('Contruccion') {
            steps {
                echo "${WORKSPACE}"
                echo "${JENKINS_HOME}"
                sh 'ls'
            }
        }
        stage('Analisis') {
            steps {
                echo 'Deploying....'
            }
        }
        stage('Push') {
            steps {
                ECHO 'Push...'
            }
        }
    }
}
