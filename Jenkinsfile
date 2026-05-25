@Library('shared-lib') _

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

    
                stage('Docker Login') {
            steps {
                sh 'echo $dockerPassword | docker login -u $dockerUsername --password-stdin'
            }
        }

        stage('Push Docker Image') {
            steps {
                sh 'docker tag java-app:v1 $dockerUsername/java-app:v1'
                sh 'docker push $dockerUsername/java-app:v1'
            }
        }
    }
}
