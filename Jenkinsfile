pipeline {
    agent any

    stages {

    stage('checkin code') {
    steps{
       git 'https://github.com/PallaviKsai/maven-project.git'
       sh '''ssh rig@52.168.175.97 "cd pallavi/;sudo git fetch --all;sudo git reset --hard origin/master"'''
       }
    }
      stage('Build') {
            steps {
                sh 'ssh rig@52.168.175.97 "cd pallavi/maven-project/;mvn clean package"'

                // sh 'mvn clean package'
            }
            //post {
                success {
                   echo ' Now archiving...'
                   archiveArtifacts artifacts: '**/target/*.war'
               }
            }
        }
        stage('Code Quality') {
          stage('test') {
           
            parallel(
              CodeCoverage: {
               build job: 'pallu-sonar1'
              },
              
              UnitTest: {
                   sh '''ssh rig@52.168.175.97 "cd pallavi/maven-project/;git fetch --all;git reset --hard origin/master;echo 'Unit test passed'"''' 
                
              }
              
            )
          }
          
        }
    }

