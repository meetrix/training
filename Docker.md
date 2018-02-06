# Docker

Docker is an application which facilitates to run application processes in containers that are like virtual machines and can then be deployed anywhere.

3 keywords that depict the meaning of Docker are:
1. develop
2. ship
3. run

In briefly the idea of Docker is about allowing the developers to **develop** applications easily, **ship** them into containers and **run** them anywhere.

You can refer the official site of Docker for more information. That is https://www.docker.com/ .

### Steps to Install Docker on Linux
##### Commands:
1. `sudo apt-get update`
- to update the OS with the latest packages

2. `sudo apt-get install apt-transport-https ca-certificates`
- to install the necessary certificates that will be required to work with the Docker site later on to download the necessary Docker packages

3. `sudo apt-key adv \ --keyserver hkp://ha.pool.sks-keyservers.net:80 \ --recv-keys 58118E89F3A912897C070ADBF76221572C52609D`
- to add the new GPG key (command will download the key with the ID 58118E89F3A912897C070ADBF76221572C52609D from the keyserver hkp://ha.pool.sks-keyservers.net:80 and adds it to the adv keychain )

4. `echo "Xenial 16.04 (LTS) ─ deb https://apt.dockerproject.org/repo ubuntu-xenial main” | sudo tee /etc/apt/sources.list.d/docker.list`
- to add the relevant site to the docker.list for the apt package manager according to the version of Ubuntu
  - Precise 12.04 (LTS) ─ deb https://apt.dockerproject.org/repo ubuntu-precise main
  - Trusty 14.04 (LTS) ─ deb https://apt.dockerproject.org/repo ubuntu-trusty main
  - Wily 15.10 ─ deb https://apt.dockerproject.org/repo ubuntu-wily main
  - Xenial 16.04 (LTS) ─ deb https://apt.dockerproject.org/repo ubuntu-xenial main

5. `sudo apt-get update`
- to update the packages on the Ubuntu system

6. `apt-cache policy docker-engine`
- to verify that the package manager is pointing to the right repository

7. `sudo apt-get update`
- to ensure all the packages on the local system are up to date

8. `sudo apt-get install linux-image-extra-$(uname -r) linux-image-extra-virtual`
- to install the linux-image-extra-*kernel packages which allows to use the aufs storage driver

9. `sudo apt-get install –y docker-engine`
- to install Docker

10. `sudo docker version`
- to view the details of the installed Docker version

11. `sudo docker info`
- to view more details such as number of containers, number of images, the storage driver used by Docker, the root directory used by Docker and the execution driver used by Docker



## Dockerizing a Node.js Web app

1) Create DockerHub account if you don’t have one. So that you can add your projects to DockerHub
https://hub.docker.com/

2) Create a folder named Docker in your local machine and create a DockerFile inside it
command to run in terminal(to create a Dockerfile inside the Docker folder)
	- `touch Dockerfile`

  ##### Dockerfile content:
	
	FROM node:carbon
  
	# Create app directory
	WORKDIR /usr/src/app

	# Install app dependencies
	# A wildcard is used to ensure both package.json AND package-lock.json are copied
	# where available (npm@5+)
	COPY package*.json ./

	RUN npm install
	# If you are building your code for production
	# RUN npm install --only=production

	# Bundle app source
	COPY . .

	EXPOSE 8080
	CMD [ "npm", "start" ]

3) Create a .dockerignore file in the same directory as your Dockerfile

	 ##### .dockerignore filecontent:

    ```
    node_modules      
    npm-debug.log
    ```
    
4) Copy the project content into the Docker folder

5) Run commands to build the Docker image
   - `docker build -t <your username>/node-web-app .`

6) Command for listing image
   - `docker images`

7) Command to run the image
   - `docker run -p 49160:8080 -d <your username>/node-web-app`    
	 49160-local port   
	 8080-docker port    
		 (you can use different port numbers)

8) Command to print the output of your app  

	 //get container ID    
	 - `docker ps`   
  
	 //print app output   
	 - `docker logs <container id>`    
   
	 //Running on http://localhost:8080

9) If you need to go inside the container
   - `docker exec -it <container id> /bin/bash`
	
10) To test your app, get the port of your app that Docker mapped:
		- `docker ps`

    ###### Example:

	  ID | IMAGE | COMMAND | ... | PORTS  
    --- | --- | --- | --- | ---
	  ecce33b30ebf | <your username>/node-web-app:latest | npm start | ... | 49160->8080    

	  //In the example above, Docker mapped the 8080 port inside of the container to the port 49160 	on your machine.

11) Now you can call your app using curl (install if needed via: sudo apt-get install curl):
    - `curl -i localhost:49160` (according to the example)
