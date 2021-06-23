# Flow-2: Create a new Docker Image, Run as Container and Push to Docker Hub

## Pre-requisite Step
- Create your Docker hub account. 
- https://hub.docker.com/
- **Important Note**: In the below listed commands wherever you see **nirajp82** you can replace with your docker hub account id. 
- Create a docker file in any directory. Here I am using Powershell and notepad++
- -  New-Item -Path . -name Dockerfile -ItemType "file"
- - notepad++.exe .\Dockerfile
- - Copy/Paste following content in Dockerfile
   FROM nginx
   COPY index.html /usr/share/nginx/html
- Create Index.html: New-Item -path . -name index.html -ItemType "file"

## Step-1: Run the base Nginx container
- Access the URL http://localhost
```
docker run --name mynginxdefault -p 80:80 -d nginx
docker ps
docker stop mynginxdefault
```

## Step-2: Create Dockerfile and copy our customized index.html
- **Dockerfile**
```
FROM nginx
COPY index.html /usr/share/nginx/html
```

## Step-3: Build Docker Image & run it
```
docker build -t nirajp82/my_first_docker_image:v1 .
docker run --name myfirstdockerimage -p 4081:80 -d nirajp82/my_first_docker_image:v1

Replace your docker hub account Id
docker build -t <your-docker-hub-id>/my_first_docker_image:v1 .
docker run --name myfirstdockerimage -p 4081:80 -d <your-docker-hub-id>/my_first_docker_image:v1
```

## Step-4: Tag & push the Docker image to docker hub
```
docker images
docker tag nirajp82/my_first_docker_image:v1 nirajp82/my_first_docker_image:v1-release
docker push nirajp82/my_first_docker_image:v1-release

Replace your docker hub account Id
docker tag <your-docker-hub-id>/mynginx_image1:v1 <your-docker-hub-id>/mynginx_image1:v1-release
docker push <your-docker-hub-id>/mynginx_image1:v1-release
```
## Step-5: Verify the same on docker hub
- Login to docker hub and verify the image we have pushed
- Url: https://hub.docker.com/repositories

* Reference: https://github.com/stacksimplify/docker-fundamentals/blob/master/04-Build-new-Docker-Image-and-Run-and-Push-to-DockerHub/README.md
