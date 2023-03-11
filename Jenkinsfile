pipeline {
    agent {
        label 'master'
    }
    environment {
        AWS_ACCOUNT_ID="aws-credentials"
        AWS_DEFAULT_REGION="eu-central-1"
        IMAGE_REPO_NAME="my-nginx"
        IMAGE_TAG="v1"
        REPOSITORY_URI = "064055967665.dkr.ecr.eu-central-1.amazonaws.com/terraformecr"
    }
    stages {
        stage('push to ecr') {
        agent {
            label 'master'
        }
        steps {
                script{
                    docker.withRegistry("https://064055967665.dkr.ecr.eu-central-1.amazonaws.com/terraformecr", "ecr:eu-central-1:aws-credentials") {
                    docker.image("${IMAGE_REPO_NAME}").push()
                    }
                    
                }
            }
        }
    }
}
