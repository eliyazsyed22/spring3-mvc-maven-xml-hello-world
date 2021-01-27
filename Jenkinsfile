pipeline{
    agent any
    tools{
        maven "maven3"
    }
    stages{
        stage('scm'){
            steps{
                git credentialsId: 'maven', url: 'https://github.com/eliyazsyed22/spring3-mvc-maven-xml-hello-world.git'
            }
        }
        stage('mvn build'){
            steps{
                sh "mvn clean package"
            }
        }
    }
}    
        
        
        
        
        
