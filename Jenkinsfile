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
    }
}
