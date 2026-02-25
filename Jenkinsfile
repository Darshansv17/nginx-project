pipeline {
  agent any
  
  environment{
    IMAGE_TAG = "${env.BUILD_NUMBER}"
  }
   
    stages {
     stage('checkout'){
       steps{ 
          git branch: 'main', url: 'https://github.com/Darshansv17/nginx-project.git' 
       }
     }

     stage('Build Docker Image'){
       steps{
         sh " docker build -t my-nginx:V${IMAGE_TAG} ."
       }
     }

     stage('Tag Docker Image'){
       steps{
         sh " docker tag my-nginx:V${IMAGE_TAG} 315354952551.dkr.ecr.eu-north-1.amazonaws.com/darshan/dokerimages:V${IMAGE_TAG}"
       }
     }

     stage('Authentication To ECR'){
       steps{
         sh """ aws ecr get-login-password --region eu-north-1 |\
         docker login --username AWS --password-stdin 315354952551.dkr.ecr.eu-north-1.amazonaws.com"""
       }
     }

     stage('Push to ECR'){
       steps{
         sh " docker push 315354952551.dkr.ecr.eu-north-1.amazonaws.com/darshan/dokerimages:V${IMAGE_TAG}"
       }
     }
   }
  }
    
