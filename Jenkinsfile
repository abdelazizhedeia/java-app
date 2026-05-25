@Library('shared-lib@master') _

pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git url: 'https://github.com/abdelazizhedeia/java-app', branch: 'master'
            }
        }

        stage('Build') {
            steps {
                buildJavaApp()
            }
        }

        stage('Docker Build') {
            steps {
                buildDockerImage()
            }
        }
    }
}
