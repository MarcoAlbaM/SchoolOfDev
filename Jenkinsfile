pipeline {
    agent any
       
    stages {
        stage('Checkout'){
                steps {
                   checkout scm
                }    
        }
        stage('building') {
            steps {
                sh 'docker build . -t minecraftserver:$BUILD_NUMBER'
            }
        }
        stage('Analysis') {
            steps {
                echo 'Analysis Final Final'
            }
        }
        stage('Push') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'DockerHubCredencial', passwordVariable: 'DockerHubPass', usernameVariable: 'DockerHubUser')]) {
                    sh """ 
                    docker login -u ${DockerHubUser} -p ${DockerHubPass}
                    docker image tag minecraftserver:$BUILD_NUMBER maamadmin/cicdassigment:$BUILD_NUMBER
                    docker image push maamadmin/cicdassigment:$BUILD_NUMBER
                    """
                }
            }
        }
        stage('Deploy') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'DockerHubCredencial', passwordVariable: 'DockerHubPass', usernameVariable: 'DockerHubUser')]) {
                    sh 'docker login -u ${DockerHubUser} -p ${DockerHubPass}'
                    sh 'docker run -d --name minecraftserverconta -p 25565:25565 maamadmin/cicdassigment:latest'
                    sh 'docker ps'
                }
            }
        }
         stage('CleanUp') {
                steps {
                   sh """
                   docker kill \$(docker ps -q)
                   docker system prune -a -f
                   """
                }
        }
    }
}
