pipeline {
    agent any 
    stages {
        stage(‘SCM’) { 
            steps {
                git 'https://github.com/ManjulaNaga/sample_project.git'
            }
        }
        stage(‘Maven’) { 
            steps {
                 sh 'mvn clean compile package sonar:sonar'
            }
        }
        stage(’SonarqubeAnalysis’) { 
            steps {
                    // requires SonarQube Scanner 2.8+
    			def scannerHome = tool 'sonarqube'
    			withSonarQubeEnv('sonarqube') {
     			sh "${scannerHome}/bin/sonar-scanner"
                }
            }
        }
    }
}

