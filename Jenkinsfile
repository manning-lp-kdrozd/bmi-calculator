pipeline {
    agent {
        docker {
            image 'sonarsource/sonar-scanner-cli:latest'
        }   
    }
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
                timeout(unit: 'SECONDS', time: 60) {
                    waitForQualityGate abortPipeline: true
                }
            }
        }
    }
}




