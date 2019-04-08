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
            steps {
              sample_project {
                nexusVersion('nexus2')
                protocol('http')
                nexusUrl('35.237.58.180:8080/nexus')
                groupId('manju.com')
                version('.01')
                repository('sample_project')
                credentialsId('44620c50-1589-4617-a677-7563985e46e1')
                artifact {
                    artifactId('nexus-artifact-uploader')
                    type('jar')
                    classifier('debug')
                    file('nexus-artifact-uploader.jar')
                }
                artifact {
                    artifactId('nexus-artifact-uploader')
                    type('hpi')
                    classifier('debug')
                    file('nexus-artifact-uploader.hpi')
                }
              }
            }
        }
      
    }
}

