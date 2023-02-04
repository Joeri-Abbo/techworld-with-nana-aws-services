## Demo project for Module 6 - Deploy to EC2 server from Jenkins Pipeline

In this demo I used the droplet from module 5 and installed Jenkins on it.
We will deploy the app from java-maven-app to an EC2 server by using docker.

### AWS Preparation

I used an existing admin user to create a new EC2 instance.
The instance is a t2.micro because this one is in the free tier.
After creating the instance I added a new rule to the security group to allow port 22 and 3000 for inbound requests.
I then went in the instance using ssh.
First I updated the instance and installed docker.
Then I created a new user to run the app.
Because I don't want to run the app as root or as ec2-user because it would be a bad practice.

### Docker preparation

After installing docker i added the new user to the docker group.
Then I logged in as the new user and started the docker service.
After that I started a new Redis container to validated the docker service is running.

Then i used docker login to login to the docker hub to allow me to pull the image from the docker hub.
Then i runned the container and validated that the app is running on port 3000 at on the public ip of the instance.

### Jenkins Preparation

I install SSH agent plugin on Jenkins & add SSH key for EC2 instance login in Jenkins credentials.
After validating the jenkins server could use ssh to connect to the EC2 instance.
I changed the jenkins file to deploy to EC2.

Then I triggered the pipeline and validated that the app is running on port 3000 at on the public ip of the instance with
its new version.


### Docker compose
Then I created a docker-compose file to run the app and the postgres container.
Firstly I runned it local to validated if the docker-compose file was correctly configured.
Then I pushed the docker-compose file to the github repo.

Then I changed the jenkins file to deploy the app with docker-compose.
Then I triggered the pipeline and validated that the app is running on port 3000 at on the public ip of the instance with its new version.