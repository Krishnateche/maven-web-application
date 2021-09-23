node
{
 def mavenHome = tool name: "maven3.6.2"
 properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5'))])
 stage('CheckoutCode')
 {
   git branch: 'development', credentialsId: '1d7e5f63-f519-4806-b8a0-ca6f5a0ae6a1', url: 'https://github.com/Krishnateche/maven-web-application.git'
 }
 stage('build')
 {
 sh "${mavenHome}/bin/mvn clean package"
 }
  /*
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
*/
    
}
