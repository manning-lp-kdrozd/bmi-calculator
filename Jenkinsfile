pipeline {
    agent any 
    stages {
        stage('SCA') {
            steps {
                withSonarQubeEnv('sonarqube') {
                    sh 'sonar-scanner'
                }
            }
        }
    }
}