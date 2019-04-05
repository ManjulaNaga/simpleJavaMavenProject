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
                 sh 'mvn clean compile package'
            }
        }
        stage(‘NexusPublish’) {
            steps{
                nexusPublisher nexusInstanceId: 'gcpnexus',nexusRepositoryId: 'sample_project', 
                    packages: [[$class: 'MavenPackage', 
                                mavenAssetList: [[classifier: '', extension: '', filePath: 'target/myMavenPipelineProject-0.0.1-SNAPSHOT.war']], 
                                mavenCoordinate: [artifactId: 'myMavenPipelineProject-war', groupId: 'org.com', 
                                                  packaging: 'war', version: '0.01']]]
            }
        }
      
    }
}

