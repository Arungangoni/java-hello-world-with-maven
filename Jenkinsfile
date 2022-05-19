pipeline{
    agent any
    stages{
        stage('Submit stack'){
            steps{
                sh "aws cloudformation create-stack --stack-name s3bucket --templatebody file://./s3cft.yaml --region 'us-east-1'"
            }
        }
}
}
