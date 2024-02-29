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
                sh "docker build -t jakepaulsmith/nginx ./nginx"
                sh "docker build -t jakepaulsmith/flask-app ./python"              
            }
        }
        stage("Run Containers"){
            steps{
                sh "docker run -d --name flask-app flask-app"
                sh "docker run -d -p 80:80 --name nginx nginx"              
            }
        }
        
    }



}
