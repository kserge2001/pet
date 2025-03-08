pipeline {
    agent any

    tools {
        maven 'maven'
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn compile'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('trivy scan') {
            steps {
              sh "trivy fs --severity CRITICAL,HIGH --exit-code 1 --format table -o maven_dependency.html ."  
            }
        }
    }
}