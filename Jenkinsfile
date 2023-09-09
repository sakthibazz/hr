pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout your GitHub repository
                git 'https://github.com/sakthibazz1/hrportal.git'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                script {
                    // Run SonarQube analysis using the SonarScanner
                    def scannerHome = tool 'SonarScanner' // Configure SonarScanner tool in Jenkins
                    withSonarQubeEnv('hrportal-sonarqube') {
                        sh """
                            ${scannerHome}/bin/sonar-scanner -Dsonar.host.url=http://localhost:9091
                        """
                    }
                }
            }
        }
    }
}
