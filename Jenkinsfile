pipeline {
    agent any

    stages {
        stage('checkin code') {
            steps {
                git 'https://github.com/PallaviKsai/maven-project.git'
                //sh '''ssh rig@52.168.175.97 "cd pallavi/;sudo git fetch --all;sudo git reset --hard origin/master"'''
                sh '''ssh rig@52.168.175.97 "cd pallavi/;sudo rm -rf maven-project;sudo git clone https://github.com/PallaviKsai/maven-project.git"'''
                }
           }
      stage('Build') {
            steps {
                sh 'ssh rig@52.168.175.97 "cd pallavi/maven-project/;sudo mvn clean package"'
                // sh 'mvn clean package'
            }
        }
       stage('Code Quality') { 
              steps {
              sh '''ssh rig@52.168.175.97 "cd pallavi/maven-project/;sudo /opt/sonarqube/sonar-scanner-3.0.3.778/bin/sonar-scanner"'''
              }
       
          }
        stage("Upload artifact") {
            
            def server = Artifactory.server 'Artifact'
            def uploadSpec = """{
  "files": [
    {
      "pattern": "webapp/target/*.war",
      "target": "maven-local/"
    }
 ]
}"""
server.upload(uploadSpec)
            
        }
    }
}
    
