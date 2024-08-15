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
        
        stage('UNIT testing') {
            steps {
                script {
                    sh 'mvn test'
                }
            }
        }
        
        stage('Integration testing') {
            steps {
                script {
                    sh 'mvn verify -DskipUnitTests'
                }
            }
        }
        
        stage('Maven build') {
            steps {
                script {
                    sh 'mvn clean install'
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
