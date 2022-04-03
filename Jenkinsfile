pipeline {
    agent any
    stages {
        stage('Static Code Analysis') {
            steps {
                withSonarQubeEnv('sonarqube') {
                    sh 'sonar-scanner'
                }
            }
        }
        stage("Quality Gate"){
            steps {
                timeout(time: 2, unit: 'MINUTES') {
                    def qg = waitForQualityGate()
                    if (qg.status != 'OK') {
                        error "Pipelin. aborted due to quality gate failure: ${qg.status}"
                    }
                }
            }
        }
    }
}

