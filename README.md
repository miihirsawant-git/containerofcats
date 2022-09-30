# Overview
Web Application to display cats in a container
1. Hosting docker container on AWS ECS Cluster
2. Orchestration with kubernetes pods inside Docker container

## Build the docker image
docker build -t containerofcats .

## Test the image by running a container
docker run -t -i -p 80:80 containerofcats

## Upload image to docker hub
docker login --username <USER>
docker images
docker push <USER>/containerofcats

## ECS Hosting
1. Creating an [ECS Cluster](../containerofcats/reference/1.png)
2. Creating a [task definition](../containerofcats/reference/2.png)
3. Set appropriate [Port Mapping](../containerofcats/reference/3.png) 
4. Final Result
![Demogrid](../containerofcats/reference/4.png)

## Orchestration with Kubernetes-in-Docker
1. Create a kubernetes-in-docker [cluster](../containerofcats/kb-reference/1.png)
2. Apply the deploy yaml configuration for replicas
3. Apply the services yaml configuration for networking

    [Output Reference for Pods](../containerofcats/kb-reference/2.png)

4. Apply the ingress controller deployement
    ```
    kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.1.3/deploy/static/provider/cloud/deploy.yaml
    ```
    
-   [Reference 1](../containerofcats/kb-reference/3.png)
-   [Reference 2](../containerofcats/kb-reference/4.png)

5. Apply the [ingress](../containerofcats/kb-reference/5.png) configuration and set the port forward to nginx-controller
    ```
    kubectl -n ingress-nginx --address 0.0.0.0 port-forward svc/ingress-nginx-controller 80
    ```
6. Final Result
![Demogrid](../containerofcats/kb-reference/6.png)