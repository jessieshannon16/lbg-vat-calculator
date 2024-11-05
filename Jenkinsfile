pipeline{
    agent any

    stages{
        stage('Install'){
            steps{
                sh "npm install"
            }
        }
        stage('Test'){
            steps{
                sh "npm test"
            }
        }
        stage('SonarQube Analysis') {
            environment{
                scannerHome = tool 'sonarqube'
            }
            steps{
                withSonarQubeEnv('sonarqube-1'){
                    sh "${scannerHome}/bin/sonar-scanner"
                }
                timeout(time: 10, unit: 'MINUTES'){
                    waitForQualityGate abortPipeline: true
                }
            }
        }

    }
}