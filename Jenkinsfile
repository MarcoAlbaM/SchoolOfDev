pipeline {
    agent any

    stages {
        stage('building') {
            steps {
                sh 'docker build . -t minecraftserver:latest'
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
                    sh """ 
                    docker login -u ${DockerHubUser} -p ${DockerHubPass}
                    docker image tag minecraftserver:latest maamadmin/cicdassigment:latest
                    docker image push maamadmin/cicdassigment:latest 
                    """
                }
            }
        }
    }
}
