pipeline {
    agent {
        label 'jenkins-agent'
    }

    tools {
        jdk 'jdk:11'
        maven 'maven-354'
    }

    environment {
        dockerUsername = credentials('dockerusername')
        dockerPassword = credentials('dockerpassword')
    }

    stages {

        stage('Build Java App') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }

        stage('Test Java App') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Archive Java App') {
            steps {
                archiveArtifacts artifacts: '**/*.jar', followSymlinks: false
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t java-app:v1 .'
            }
        }
        }
    }
}
