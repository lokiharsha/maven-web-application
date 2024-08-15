pipeline {
    agent any
    
    stages {
        stage('Git Checkout') {
            steps {
                script {
                    git branch: 'master', url: 'https://github.com/lokiharsha/maven-web-application.git'
                }
            }
        }
        
        
       
        
        stage('Static code analysis') {
            steps {
                script {
                    withSonarQubeEnv(credentialsId: 'cred') {
                        sh 'mvn clean package sonar:sonar'
                    }
                }
            }
        }
        
    }
}
