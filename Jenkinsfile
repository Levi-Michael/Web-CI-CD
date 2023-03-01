pipeline {
    agent {
        label 'docker'
    }
	
    stages {
        stage('Git-Checkout') {
            steps {
                    echo "Checking out from Git Repo";
		            git branch: 'main', credentialsId: '7d09ec26-8a86-48cc-b141-5c2141548065', url: 'https://github.com/Levi-Michael/docker-web.git';
            }
        }
        stage('Clean ') {
            steps {
                    echo "Clean old builds";
                     /* Put in the actual Code for Executing Build.bat file from your Git Repo here */
                    sh 'sudo docker ps -aq | xargs docker stop | xargs docker rm'

            }
        }
        stage('Build') {
            steps {
                    echo "Building the checked-out project!";
                     /* Put in the actual Code for Executing Build.bat file from your Git Repo here */
                    sh 'sudo docker build -t my-nginx:latest .'

            }
        }
		stage('Deploy') {
            steps {
                  echo "Deploying to Stage Environment for more tests!";
                  sh 'sudo docker run --name my-nginx -p 80:80 -d my-nginx'
            }
        }
        stage('Test') {
            steps {
                  echo "Running tests!";
                  sh 'sudo curl localhost'
            }
        }
    }
    post {
        always {
            echo 'This will always run'
        }
        success {
            echo 'This will run only if successful'
        }
        failure {
            echo 'This will run only if failed'
        }
        unstable {
            echo 'This will run only if the run was marked as unstable'
        }
        changed {
            echo 'This will run only if the state of the Pipeline has changed'
            echo 'For example, if the Pipeline was previously failing but is now successful'
        }
    }
}
