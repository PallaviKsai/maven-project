pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                SH 'mvn clean package'
            }
        }
        post {
            success {
                echo ' Now archiving...'
                archiveArtifacts artifacts: '**/target/*.war'
            }
        }
    }
    stage ('Deploy to Staging'){
        steps{
            build job: 'Deploy-to-staging'
        }
    }
        
        
    }

