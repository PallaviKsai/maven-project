 
    
node{
    
stage("Checkin"){
    
    build('Checkincode');
    
}

stage("Build"){
build("BuildCheckincode");

    
}
stage("Quality check"){
build("CheckQuality");

    
}
stage("Uploadartifact"){
build("Artifact Uploading");

    
}
stage("Deploy"){
build("DeploymenttoTomcat");

    
}
}
