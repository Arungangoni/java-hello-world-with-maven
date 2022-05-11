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
        stage ('Deploy') {
      steps {
        script {
          deploy adapters: [tomcat9(credentialsId: 'TOMCAT_CRED', path: '/opt/tomcat', url: 'http://3.88.129.66:7070/')], contextPath: '/foo', onFailure: false, war: 'job1/target/*.war' 
        }
      }
    }
    }
}
