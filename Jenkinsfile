pipeline{
    agent any
    tools{
        maven "maven8"
    }
    stages{
        stage('scm'){
            steps{
                git credentialsId: 'github_credentials', url: 'https://github.com/eliyazsyed22/spring3-mvc-maven-xml-hello-world.git' 
            }
        }
        stage('mvn build'){
            steps{
                sh "mvn clean package"
            }
        }
        stage('archive artifacts'){
            steps{
                archiveArtifacts artifacts: 'target/*.war', followSymlinks: false
            }
        }
        stage('deploy'){
           steps{
               withCredentials([usernameColonPassword(credentialsId: 'tomcat_credentials', variable: 'secretpassword')]) 
               {
                sh "curl -v -u admin:admin -T /var/lib/jenkins/workspace/pipelinewebsite/target/spring3-mvc-maven-xml-hello-world-1.0-SNAPSHOT.war 'http://13.233.5.188:8080/manager/text/deploy?path=/jenkins_deploy&update=true'"
                }
            }
        }
    }
}
