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
                timeout(time: 1, unit: ‘MINUTES’) {
                    waitForQualityGate abortPipeline: true
                }
            }
        }
    }
}

