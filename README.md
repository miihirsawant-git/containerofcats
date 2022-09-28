# Overview
Web Application to display cats in a container

## Build the docker image
docker build -t containerofcats .

## Test the image by running a container
docker run -t -i -p 80:80 containerofcats

## Upload image to docker hub
docker login --username <USER>
docker images
docker push <USER>/containerofcats

## Reference
1. Creating an [ECS Cluster](/container/reference/1.png)
2. Creating a [task definition](/container/reference/2.png)
3. Set appropriate [Port Mapping](/container/reference/3.png) 
4. Final Result
![Demogrid](/container/reference/4.png)