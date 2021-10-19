pipeline {
    agent any

    stages {
        stage('building') {
            steps {
                sh 'docker build . -t cicdassigment:latest'
                sh 'docker image ls'
            }
        }
        stage('Analysis') {
            steps {
                echo 'Deploying....'
            }
        }
        stage('Push') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'DockerHubCredencial', passwordVariable: 'DockerHubPass', usernameVariable: 'DockerHubUser')]) {
                    sh 'docker login -u ${DockerHubUser} -p ${DockerHubPass}'
                    sh 'docker push maamadmin/cicdassigment:latest'
                }
            }
        }
    }
}
