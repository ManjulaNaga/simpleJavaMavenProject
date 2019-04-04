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
                scannerHome = tool 'sonarqube'
            }
            steps {
                    sleep(10)
                    qualitygate = waitForQualityGate()
                    if (qualitygate.status != "OK") {
                        withSonarQubeEnv('sonarqube') {
                            sh "${scannerHome}/bin/sonar-scanner"
                        }
                    }

            }
        }
    }
}

