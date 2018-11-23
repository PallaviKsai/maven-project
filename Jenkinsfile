 node {
  
        stage('checkin code') {
            
                git 'https://github.com/PallaviKsai/maven-project.git'
                //sh '''ssh rig@52.168.175.97 "cd pallavi/;sudo git fetch --all;sudo git reset --hard origin/master"'''
                sh '''ssh rig@52.168.175.97 "cd pallavi/;sudo rm -rf maven-project;sudo git clone https://github.com/PallaviKsai/maven-project.git"'''
            
           }
      stage('Build') {
                sh 'ssh rig@52.168.175.97 "cd pallavi/maven-project/;sudo mvn clean package"'
                // sh 'mvn clean package'
        }
       stage('Code Quality') { 
              sh '''ssh rig@52.168.175.97 "cd pallavi/maven-project/;sudo /opt/sonarqube/sonar-scanner-3.0.3.778/bin/sonar-scanner"'''
       
          }
        stage('Upload artifact') {    
            
             sh 'ssh rig@52.168.175.97 "cd pallavi/maven-project/;curl -H \"X-JFrog-Art-Api:AKCp5btVgVphFs3hmxLtvRXQ5tTLXqqKJYU5smHh2YdsUfo7GGJKFMvLjrM58rARwcobmXkMA \" -T ./webapp/target/*.war \" http://52.15.238.157:8081/artifactory/local-repo/webapp.war \""' 
        }
}
    
    
