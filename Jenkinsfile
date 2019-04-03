pipeline {
    agent any 
    stages {
        stage(‘SCM’) { 
            steps {
                git 'https://github.com/ManjulaNaga/simpleJavaMavenProject.git'
            }
        }
        stage(‘Maven’) { 
            steps {
                 sh 'mvn clean compile package sonar:sonar'
            }
        }
        stage('Sonarqube') {
            environment {
                scannerHome = tool 'SonarQubeScanner'
            }
            steps {
                withSonarQubeEnv('sonarqube') {
                    sh "${scannerHome}/bin/sonar-scanner"
                }
                timeout(time: 10, unit: 'MINUTES') {
                    waitForQualityGate abortPipeline: true
                }
            }
        }
    }
}

