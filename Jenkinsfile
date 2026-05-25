@Library('shared-lib@master') _
pipeline {
    agent any

    stages {

        stage('Build Java') {
            steps {
                buildJavaApp()
            }
        }

        stage('Docker Build') {
            steps {
                dockerBuild("java-app", "v1")
            }
        }
    }
}
