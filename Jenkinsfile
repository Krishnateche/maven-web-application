node
{
    def mavenHome = tool name: "maven3.6.3"
    properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '5', numToKeepStr: '')), pipelineTriggers([pollSCM('* * * * *')])])

 stage('CheckoutCode')
 {
  git branch: 'development', credentialsId: 'dfa30a9e-f60b-4bfd-9614-e3a8f48b53c1', url: 'https://github.com/Krishnateche/maven-web-application.git'
 }

 stage('Build')
 {
 sh "${mavenHome}/bin/mvn clean package"
 }
 stage('ExecutesonarQubeReport')
{
 sh "${mavenHome}/bin/mvn sonar:sonar"
}
 stage('DeployappliIntotomcat')
{
 sshagent(['3455a364-dce2-4e0a-88c5-079e40a0aca8']) 
{
 sh "scp -o StrictHostkeyChecking=no target/maven-web-application.war ec2-user@3.108.236.152:/opt/apache-tomcat-9.0.50/webapps/"
   
}
}

}
