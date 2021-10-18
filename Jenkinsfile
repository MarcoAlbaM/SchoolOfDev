pipeline {
    agent any

    stages {
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
