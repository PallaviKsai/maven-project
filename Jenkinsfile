pipeline {
    agent any

    stages {

    stage('checkin code') {
    steps{
       git 'https://github.com/PallaviKsai/maven-project.git'
       //sh '''ssh rig@52.168.175.97 "cd pallavi/;sudo git fetch --all;sudo git reset --hard origin/master"'''
         sh '''ssh rig@52.168.175.97 "cd pallavi/;sudo rm -rf maven-project;sudo git clone https://github.com/PallaviKsai/maven-project.git"'''
       }
    }
      stage('Build') {
            steps {
                sh 'ssh rig@52.168.175.97 "cd pallavi/maven-project/;mvn clean package"'

                // sh 'mvn clean package'
            }
            post {
                success {
                   echo ' Now archiving...'
                   archiveArtifacts artifacts: '**/target/*.war'
               }
            }
        }
        stage('Code Quality') {
        
              steps {
               build job: 'pallu-sonar1'
              }
              
            
          
          }
          
        
    }
}
    
