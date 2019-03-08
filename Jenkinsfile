node {
  stage('SCM') {
    git 'https://github.com/ManjulaNaga/sample_project.git'
  }
  stage('maven') {
      sh 'mvn clean compile package sonar:sonar'
  }
  stage('SonarQube analysis') {
    // requires SonarQube Scanner 2.8+
    def scannerHome = tool 'sonarqube';
    withSonarQubeEnv('sonarqube') {
      sh "${scannerHome}/bin/sonar-scanner"
    }
  }
}
