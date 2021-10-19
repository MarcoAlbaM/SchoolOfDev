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
                echo 'Analysis'
            }
        }
        stage('Push') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'DockerHubCredencial', passwordVariable: 'DockerHubPass', usernameVariable: 'DockerHubUser')]) {
                    sh """ 
                    docker login -u ${DockerHubUser} -p ${DockerHubPass}
                    docker image tag minecraftserver:$BUILD_NUMBER maamadmin/cicdassigment:$BUILD_NUMBER
                    docker image push maamadmin/cicdassigment:$BUILD_NUMBER
                    docker system prune -a -f
                    """
                }
            }
        }
        stage('Deploy') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'DockerHubCredencial', passwordVariable: 'DockerHubPass', usernameVariable: 'DockerHubUser')]) {
                    sh 'docker login -u ${DockerHubUser} -p ${DockerHubPass}'
                    sh 'docker run -d --name minecraftserverconta -p 25565:25565 cicdassigment:latest'
                }
            }
        }
    }
}
