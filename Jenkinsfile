pipeline {
    agent any
    tools {
        maven 'Maven 3_9_9'
    }
    stages {
        stage('Build Maven') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[url: 'https://github.com/YASSINEDERBE/-Devops']]])
                bat 'mvn clean install'
            }
        }
        stage('Build docker image'){
            steps{
                bat 'docker build -t yassine437/devops-integration . '
                
            }
        }
        stage('push image to hub'){
            
            steps{
                
            script{ 
                withCredentials([string(credentialsId: 'docker1', variable: 'docker')]) {    

                    bat 'docker login -u yassine437 -p ${docker}'
                    bat 'docker push yassine437/devops-integration '
              
            } 
                
            }
                
            }
            
        }
       

    }
}
