pipeline {
    agent any

    stages {
        stage('building') {
            steps {
                sh 'docker build . -t minecraftserver:$BUILD_NUMBER'
                sh 'docker image ls'
            }
        }
        stage('Analysis') {
            steps {
                sh 'docker run -d --name minecraftserver -p 25565:25565 minecraftserver'
            }
        }
        stage('Push') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'DockerHubCredencial', passwordVariable: 'DockerHubPass', usernameVariable: 'DockerHubUser')]) {
                    sh """ 
                    docker login -u ${DockerHubUser} -p ${DockerHubPass}
                    docker image tag minecraftserver:$BUILD_NUMBER maamadmin/cicdassigment:$BUILD_NUMBER
                    docker image push maamadmin/cicdassigment:$BUILD_NUMBER
                    docker rm -f $(docker ps -a -q)
                    docker rmi -f $(docker images -a -q)
                    """
                }
            }
        }
        stage('Deploy') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'DockerHubCredencial', passwordVariable: 'DockerHubPass', usernameVariable: 'DockerHubUser')]) {
                    sh 'docker run -d --name minecraftserverconta -p 25565:25565 cicdassigment:latest'
                }
            }
        }
    }
}
