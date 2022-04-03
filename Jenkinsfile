pipeline {
    agent {
        docker { image 'sonarsource/sonar-scanner-cli' }
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