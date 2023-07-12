pipeline {
    agent any

    stages {
        stage('ECR authentication and docker login'){

            steps{
                sh '''
                aws ecr get-login-password --region us-east-2 | docker login --username AWS --password-stdin 854171615125.dkr.ecr.us-east-2.amazonaws.com
                '''
            }
        }

        stage('Making a Build') {
            steps {
                sh '''
                cd yolo5
                docker build -t shweta-jenkins-yolo5 .
                '''
            }
        }

        stage('Pushing to ECR'){
            steps {
            sh '''
            docker tag shweta-jenkins-yolo5:latest 854171615125.dkr.ecr.us-east-2.amazonaws.com/shweta-jenkins-yolo5:0.0.${BUILD_NUMBER}
            docker push 854171615125.dkr.ecr.us-east-2.amazonaws.com/shweta-jenkins-yolo5:0.0.${BUILD_NUMBER}
            '''
            }
        }

       stage('TRIGGER deploy') {
    steps {
        build job: 'Yolo5DeployFinal', wait: false, parameters: [
            string(name: '854171615125.dkr.ecr.us-east-2.amazonaws.com/shweta-jenkins-yolo5:0.0.8', value: "854171615125.dkr.ecr.us-east-2.amazonaws.com/shweta-jenkins-yolo5:0.0.${BUILD_NUMBER}")
        ]
    }
}
    }
}
