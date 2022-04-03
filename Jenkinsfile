pipeline {
    agent any
    stages {
        stage('Static Code Analysis') {
            agent {
                docker { image 'sonarsource/sonar-scanner-cli' }
            }
            steps {
                withSonarQubeEnv('sonarqube') {
                    sh 'sonar-scanner'
                }
            }
        }
    }
}