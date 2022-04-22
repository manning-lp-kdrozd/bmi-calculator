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
    stage('Quality Test') {
        steps {
            script {
            sh 'npm run coverage'
            }
        }
        post {
            always {
            step([$class: 'CoberturaPublisher', coberturaReportFile: 'output/coverage/jest/cobertura-coverage.xml'])
            }
        }
        }
        stage('Test') { 
            steps {
                sh 'npm test' 
            }
        }
    }
}