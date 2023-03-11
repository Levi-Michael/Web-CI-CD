pipeline {
    agent none
	
    environment {
        AWS_ACCOUNT_ID="aws-credentials"
        AWS_DEFAULT_REGION="eu-central-1"
        IMAGE_REPO_NAME="my-nginx"
        IMAGE_TAG="v1"
        REPOSITORY_URI = "064055967665.dkr.ecr.eu-central-1.amazonaws.com/terraformecr"
    }
    stages {
        stage('Git-Checkout') {
            agent {
                label 'master'
            }
            steps {
                echo "Checking out from Git Repo";
		        git branch: 'main', url: 'https://github.com/Levi-Michael/Web-CI-CD.git';
            }
        }
        stage('Building image') {
            agent {
                label 'master'
            }
            steps{
                script {
                dockerImage = docker.build "${IMAGE_REPO_NAME}:${IMAGE_TAG}"
                }
            }
        }
        // stage('Build') {
        //     agent {
        //         label 'master'
        //     }
        //     steps {
        //         echo "Building the checked-out project!";
        //         sh 'sudo docker build -t my-nginx:latest .'
        //     }
        // }
        stage('Pushing to ECR') {
            agent {
                label 'master'
            }
            steps{  
                script {
                        sh """docker tag ${IMAGE_REPO_NAME}:${IMAGE_TAG} ${REPOSITORY_URI}:$IMAGE_TAG"""
                        sh """docker push ${AWS_ACCOUNT_ID}.dkr.ecr.${AWS_DEFAULT_REGION}.amazonaws.com/${IMAGE_REPO_NAME}:${IMAGE_TAG}"""
                }
                }
            }
		// stage('Deploy') {
        //     agent {
        //         label 'docker'
        //     }
        //     steps {
        //         echo "Deploying to Stage Environment for more tests!";
        //         sh 'sudo docker run --name my-nginx -p 80:80 -d my-nginx'
        //     }
        // }
        // stage('Test') {
        //     agent {
        //         label 'docker'
        //     }
        //     steps {
        //         echo "Running tests!";
        //         sh 'sudo curl localhost'
        //     }
        // }
        // stage('Cleaning images') {
        //     agent {
        //         label 'master'
        //     }
        //     steps {
        //         echo "Cleaning images...";
        //         sh 'docker rmi -f $(docker images -a -q)'
        //     }
        // }
        // stage('Cleaning containers') {
        //     agent {
        //         label 'docker'
        //     }
        //     steps {
        //         echo "Clean old builds";
        //         sh 'docker rm $(docker ps -aq)'
        //     }
        // }
    }
}
