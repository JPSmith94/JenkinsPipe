pipeline {
    agent any
    stages {
        stage("Clean up"){
            steps{
                sh "bash cleanup.sh || true"
            }
        }
        stage("Build Images"){
            steps{
                sh "docker build -t nginx ./nginx"
                sh "docker build -t flask-app ./python"              
            }
        }
        stage("Run Containers"){
            steps{
                sh "docker run -d --network my-network --name flask-app flask-app"
                sh "docker run -d -p 80:80 --network my-network --name nginx nginx"              
            }
        }
        
    }



}
