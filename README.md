Lab1: Create Dockerfile, build docker image and deploy docker container on Amazon Linux EC2 

Assumptions:
Keypairs created.
Policy name EC2InstanceProfileForImageBuilderECRContainerBuilds was added in the LabRole.
EC2 instance deployed.
Docker application was installed.
ec2-user was added to the docker user group.

Instructions:
Copy AWS ECR credentials by running command aws ecr get-login --region us-east-1
Login to EC2 instance through ssh "ssh -i catsandogs ec2-user@44.205.157.125"
sudo run the copied credentials removing the environment variable
Pull images by running below
  "sudo docker pull 959528218548.dkr.ecr.us-east-1.amazonaws.com/clo835lab1-catsanddogs:cats"
   "sudo docker pull 959528218548.dkr.ecr.us-east-1.amazonaws.com/clo835lab1-catsanddogs:dogs"
Check pulled Images
   "docker images"
run and mapped docker container based on the pulled docker images
   "docker run -d -p 8080:80 096d33144375" 
   "docker run -d -p 8081:80 688195fb5e3d"   
Check and inspect container images 
   "docker ps"
   "docker inspect container_id"
Login to container with command shell
   "docker exec -it container_id bash"
Install network utility for ping command
   "apt-get update"
    "apt-get install iputils-ping"
Ping container IP address 
     "ping 172.17.0.3"
     "ping 172.17.0.2"
Run EC2 Instance IP address on the web browser with container assigned port 
   "http://44.205.157.125:8080"
    "http://44.205.157.125:8081"
Repeat steps 13 to 34 for pulling new docker image pushed to the ECR through github action. 


