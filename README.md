
Lesson 9 Demo 2
Continuous Monitoring on Docker with ELK Stack

Steps to be followed:


Step 1: Set up ELK stack on Docker





Download Docker compose file in one of the git repositories and follow the set of commands given below to initialize the ELK stack.


Fork the following repo 
https://github.com/Siraj-ul-muneera/ELKExample.git
Use this repo in Jenkins Pipeline as well. 
git clone <URL_of _repo _you _ just _ forked> 
cd ELKExample
ls -alrt

Start the ELK stack using the docker-compose command. Usually, this binary is installed on a server.  
docker-compose version



If you do not have docker compose installed please install it 

sudo apt-get install python-pip
sudo pip install docker-compose


Before starting the ELK stack, run the command given below so that elastic search is configured properly.

sudo sysctl -w vm.max_map_count=262144

Run the docker-compose command to initialize the ELK stack.

docker-compose up -d
docker ps


Open the Kibana URL using the public IP of the host and 5601 port to access the Kibana dashboard.

http://localhost:5601/app/kibana



================================
STOP HERE we have issues with Jenkins Vrs Plugin Versions

================================
Deploy spring boot application:
=====================================

In the same folder we have a dockerfile. Let us build it:
# docker build -t springboot .
Create a container with your new Image:
# docker run -d -p 81:8080 -v /var/log/:/var/log/  springboot
Check the container is running:
# docker ps -a --latest
GO to browser:
localhost:81
===============================================



We can see the Docker container deployed on the Docker host using the command:

docker ps | grep springbootapp



Step 3: Run the Spring Boot application and check the logs in Kibana

Access the Spring Boot web application and perform some random activity so that the logs will be pushed to ELK stack.


http://localhost:81

Check the logs pushed to ELK stack in Kibana.

Navigate to the Kibana dashboard. Select Index Management from the navigation bar on the left. You can see the logs created.
http://localhost:5601/app/kibana



