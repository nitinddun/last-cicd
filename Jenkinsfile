pipeline {
    agent any

    stages {
        stage('Docker Build') {
            steps {
                sh '''
                git@github.com:nitinddun/last-cicd.git main
                sudo docker build -t 767243193153.dkr.ecr.ap-northeast-1.amazonaws.com/pipeline:latest:$BUILD_NUMBER .
                # login to ecr 
                aws ecr get-login-password --region ap-northeast-1 | docker login --username AWS --password-stdin 767243193153.dkr.ecr.ap-northeast-1.amazonaws.com
                #push the image to ecr 
                docker push 767243193153.dkr.ecr.ap-northeast-1.amazonaws.com/pipeline:latest:$BUILD_NUMBER
                '''
            }
        }
        // stage('EKS Deploy') {
        //     steps {
        //         sh '''
        //         # helm 
        //         helm upgrade -i static-dev static -n dev --set image.tag=$BUILD_NUMBER
        //         '''

            }
        }
    
