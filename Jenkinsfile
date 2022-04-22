pipeline {
    agent {
        docker {
            image 'node:16.13.1-alpine'            
        }
    }
    stages {
        stage('Build') { 
            steps {
                sh 'npm install' 
            }
        }
        stage('Test') { 
            steps {
                sh 'CI=true npm test' 
            }
        }
        stage('Quality Test') {
            steps {
                sh 'CI=true npm test -- --coverage'
            }
            post {
                always {
                    step([$class: 'CoberturaPublisher', coberturaReportFile: 'output/coverage/jest/cobertura-coverage.xml'])
                }
            }
        }
    }
}