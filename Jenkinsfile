pipeline {
    agent {
        docker { image 'node:16.13.1-alpine' }
    }
    stages {
        stage('Static Code Analysis') {
            steps {
                withSonarQubeEnv('sonarqube') {
                    sh 'sonar-scanner'
                }
            }
        }
    }
}