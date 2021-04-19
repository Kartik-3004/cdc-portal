pipeline {
    agent any
    environment {
        CI = 'true'
    }

    stages {
        stage('Cloning Git') {
            steps {
                nodejs(nodeJSInstallationName: 'node14'){
                    git 'https://github.com/Kartik-3004/cdc-portal.git'
                }  
            }
        }
        stage('Install dependencies') {
            steps {
                nodejs(nodeJSInstallationName: 'node14'){
                    sh 'npm install'
                }  
            }
        }
        stage('Build') {
            steps {
                nodejs(nodeJSInstallationName: 'node14'){
                    sh 'npm build'
                }
            }
        }
        stage('Test') {
            steps {
                nodejs(nodeJSInstallationName: 'node14'){
                    sh 'npm test'
                }
            }
        }
    }
}
