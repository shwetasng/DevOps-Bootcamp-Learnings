## USING ECR SERVICE PROVIDED BY AWS:
- first go and create a repository
  <img width="960" alt="image" src="https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/310fdb97-9c0d-4bbc-a33c-72fcbb3813c6">
  <img width="960" alt="image" src="https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/a9da68f8-5ca8-4f40-ab8f-a7b9fa8d30a5">
  
- After creating the repository select it and click on view push commands:
  <img width="960" alt="image" src="https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/23d718a4-dfe5-4016-b50a-099b55f90260">
  <img width="617" alt="image" src="https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/5b1bda6d-c153-4f71-9622-087a0ef0de44">

- then these commands will go into the Build.Jenkins file: refer [Build.Jenkinsfile](Build.Jenkinsfile)

```text
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
```

  


