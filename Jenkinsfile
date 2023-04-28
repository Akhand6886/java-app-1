pipeline {

    agent any

    stages {

        stage("Git Checkout"){
            steps {
                git branch: 'main', url: 'https://github.com/Akhand6886/java-app-1.git'
            }
        }

        stage("Unit Testing"){
            steps {
                sh 'mvn test'
            }
        }

        stage("Integration Testing"){
            steps {
                sh 'mvn verify -DskipUnitTests'
            }
        }

        stage("Build"){
            steps {
                sh 'mvn clean install'
            }
        }

        stage("Static Code Analysis"){
            steps {
                script {
                    withSonarQubeEnv(credentialsId: '569f2af5-9f71-4f36-a2b6-94bf63e88856') {
                        sh 'mvn clean package sonar:sonar'
                    }
                }
            }
        }

        stage("Quality Gate Analysis"){
            steps {
                script {
                   waitForQualityGate abortPipeline: false, credentialsId: '569f2af5-9f71-4f36-a2b6-94bf63e88856' 
                }
            }
        }
    }
}
