

# Web CI/CD Pipeline Project

This project demonstrates a Continuous Integration and Continuous Deployment (CI/CD) pipeline using Jenkins, Docker, and Nginx. The pipeline automates the process of building, testing, and deploying a web application within an Nginx container.

## Project Structure

- **Dockerfile**: Defines the Docker image for the Nginx web server.
- **Jenkinsfile**: Contains the Jenkins pipeline script with separate stages for Continuous Integration (CI) and Continuous Deployment (CD).
- **index.html**: A sample HTML file served by Nginx.

## Pipeline Overview

The Jenkins pipeline is divided into two main stages:

1. **Continuous Integration (CI)**:
   - **Git Checkout**: Retrieves the latest code from the repository.
   - **Build Image**: Builds the Docker image using the Dockerfile.
   - **Push to ECR**: Pushes the built image to Amazon Elastic Container Registry (ECR).
   - **Clean Master Images**: Cleans up local Docker images on the master node to free up space.

2. **Continuous Deployment (CD)**:
   - **Pull from ECR**: Pulls the Docker image from ECR.
   - **Run Image**: Deploys the Docker container on the slave node.

## Prerequisites

- **Jenkins**: Ensure Jenkins is installed and running.
- **Docker**: Docker should be installed on both master and slave nodes.
- **Amazon ECR**: Set up an ECR repository to store Docker images.
- **AWS CLI**: Configure AWS CLI with appropriate permissions for ECR operations.

## Setup Instructions

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/Levi-Michael/Web-CI-CD.git
   ```

2. **Configure Jenkins Job**:
   - Create a new Pipeline job in Jenkins.
   - In the Pipeline section, set the Definition to "Pipeline script from SCM".
   - Set the SCM to Git and provide the repository URL.
   - Specify the branch to build (e.g., `main`).
   - Save the job configuration.

3. **Configure AWS Credentials in Jenkins**:
   - Install the "AWS Credentials" plugin in Jenkins.
   - Add AWS credentials (Access Key ID and Secret Access Key) in Jenkins' credentials store.
   - Reference these credentials in the Jenkinsfile.

4. **Run the Pipeline**:
   - Trigger the Jenkins job manually or set up a webhook for automatic triggering on code commits.
   - Monitor the pipeline stages in Jenkins to ensure successful execution.

## Notes

- Ensure that the Jenkins slave node has the necessary permissions and network access to pull images from ECR and run Docker containers.
- Modify the `index.html` file to customize the web application's content.
- Update the `Dockerfile` and `Jenkinsfile` as needed to fit specific project requirements.

For more information on setting up CI/CD pipelines with Jenkins and Docker, refer to the following resources:

- [How to build a CI/CD pipeline with GitHub Actions in four simple steps](https://github.blog/enterprise-software/ci-cd/build-ci-cd-pipeline-github-actions-four-steps/)
- [ci-cd-pipeline · GitHub Topics](https://github.com/topics/ci-cd-pipeline)

These resources provide comprehensive guides and examples to help you understand and implement CI/CD pipelines effectively. 

## Contact

Feel free to reach out for questions or collaboration opportunities or suggestions, open an issue or contact me directly through my [GitHub profile](https://github.com/Levi-Michael).
