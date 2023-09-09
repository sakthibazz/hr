pipeline {
    agent any
    tools {
        jdk 'Java 17' // Use the name you specified in the JDK configuration
    }

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
                            ${scannerHome}/bin/sonar-scanner -Dsonar.host.url=http://172.31.18.169:9091
                        """
                    }
                }
            }
        }
    }
}
