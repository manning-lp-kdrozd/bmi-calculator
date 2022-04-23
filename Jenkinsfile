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
                publishCoverage(
                    adapters: [
                        cobertura(coberturaReportFile: 'coverage/cobertura-coverage.xml', thresholds: [[unhealthyThreshold: 70.0, unstableThreshold: 0.0]])
                    ],
                    sourceFileResolver: sourceFiles('STORE_ALL_BUILD'),
                )
            }
         
        }
    }
}