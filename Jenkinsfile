pipeline {
    agent any

    stages {

    stage('checkin code') {
     steps{
       //git credentialsId: '46e5a3f3-103d-4b51-bab3-148d1b6fc773', url: 'https://gitlab.com/ARUNMOHANRAJ471/whatsviz.git'
       git url :'https://github.com/PallaviKsai/maven-project.git'
       sh '''ssh rig@52.168.175.97 "cd pallavi/;sudo git clone https://github.com/PallaviKsai/maven-project.git"'''
       }
     }
    stage('Build') {
      steps {
             sh 'ssh rig@52.168.175.97 "cd pallavi/maven-project/;pwd;touch success"'
           // sh 'mvn clean package'
            }
        }
    }
    }
