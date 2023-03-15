
TOPIC

    A Jenkins CI\CD pipeline project with Nginx container base on Docker engine.

SHORT DESCRIPTION

    A Jenkinsfile pipeline CI\CD with logic splite between CI and CD 
    
    The CI will run on the master and will execute Git-Checkout, Build-Image, Push-To-ECR, Cleaning-master-images
    
    The CD will run on the slave and will execute Pull-From-ECR, Run-Image

	
HOW TO RUN
	
    Create a SCM job on your jenkins and point it to this git.
