pipeline{
    agent any

    tools {
         maven 'maven3'
        
    }

    stages{
        stage('checkout'){
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'github access', url: 'https://github.com/sreenivas449/java-hello-world-with-maven.git']]])
            }
        }
        stage('build'){
            steps{
               sh 'mvn package'
            }
        }
        stage(deploy){
            steps{
                sshagent(['deploy_user']){
                    sh "scp -o StrictHostKeyChecking=no /job1/target/original-jb-hello-world-maven-0.4.0.jar ec2-user@3.88.129.66:/opt/tomcat/apache-tomcat-9.0.48/webapps"
                }
      }
        
    }
    }
}
