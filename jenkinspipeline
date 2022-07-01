node{
def mavenHome =  tool name: "maven3.8.1"
stage('CheckOutCode')
{
git credentialsId: 'ab8ee02e-5cba-4bcb-b591-79fd31a9f38d', url: 'https://github.com/sushanthdevops/maven-web-application.git'
}
stage('Build')
{
sh "${mavenHome}/bin/mvn clean package"
}
stage('DeployIntoTomcatContainer')
{
sshagent(['66c4a6d5-919b-4498-8366-507380c4eb7b']){
 sh "scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/pipeline-project/target/maven-web-application.war ubuntu@3.91.64.121:/opt/apache-tomcat-9.0.64/webapps"

}
}
stage('SendEmailNotification')
{
emailext body: 'all the build is comleted', subject: 'buildover', to: 'sushanthm554@gmail.com'
}










}
