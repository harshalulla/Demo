node{
 def WORKSPACE = "/var/jenkins_home/workspace/demo"
 def dockerImageTag = "demo${env.BUILD_NUMBER}"

 try{
    stage('Clone Repo'){
         git url: 'https://github.com/harshalulla/Demo.git'
         credentialsId:'Harshalulla'
         branch: 'main'
    }
    stage('Build Docker'){
         dockerImage = docker.build("demo:${env.BUILD_NUMBER}")
    }
    stage('Deploy Docker'){
         echo "Docker Image Tag Name : ${dockerImageTag}"
         sh "docker stop demo || true && docker rm demo || true"
         sh "docker run --name demo -d -p 8081:9000 demo:${env.BUILD_NUMBER}"
    }
 }catch(e){
    throw e
 }
}