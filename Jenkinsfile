pipeline{
    agent any

    stages{
        stage('Checkout'){
            steps{
                git branch: 'main', url: 'https://github.com/jessieshannon16/lbg-vat-calculator.git'
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
            }
        }

    }
}