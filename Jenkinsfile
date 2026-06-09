pipeline {

    agent any

    tools {
        jdk 'JDK21'
        maven 'Maven3'
    }

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/kishore100923/java-devops-demo.git'
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage('Docker Build') {
            steps {
                bat 'docker build -t java-devops-demo:v1 .'
            }
        }

        stage('Docker Run') {
            steps {
                bat 'docker rm -f java-app || exit 0'
                bat 'docker run -d --name java-app java-devops-demo:v1'
            }
        }
    }
}
