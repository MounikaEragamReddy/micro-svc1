pipeline {
    agent any

    stages {
        stage('Docker build') {
            steps {
                sh '''
                #docker build
                sudo docker build -t 496501836491.dkr.ecr.ap-southeast-1.amazonaws.com/static-apache:$BUILD_NUMBER .
                #login to ecr
                aws ecr get-login-password --region ap-southeast-1 | sudo docker login --username AWS --password-stdin 496501836491.dkr.ecr.ap-southeast-1.amazonaws.com
                # push the image to ecr
                sudo docker push 496501836491.dkr.ecr.ap-southeast-1.amazonaws.com/static-apache:$BUILD_NUMBER
                '''
            }
        }
        stage('EKS deploy') {
            steps {
                sh '''
                # apply kubectl
                cd k8s/
                ./kubectl get  pods
                kubectl apply -f .
                '''
            }
        }
    }
}