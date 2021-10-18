pipeline {
    agent any

    stages {
        stage('checking') {
            steps {
                checkout scm           
            }
        stage('building') {
            steps {
                echo "${WORKSPACE}"
                echo "${JENKINS_HOME}"
                sh 'ls'             
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
