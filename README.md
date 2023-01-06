# kubernetes-devops-security

## Fork and Clone this Repo

## Clone to Desktop and VM
A VM is a virtual machine like 

## NodeJS Microservice - Docker Image -
`docker run -p 8787:5000 imambo/node-service:v1`

`curl localhost:8787/plusone/99`
 
## NodeJS Microservice - Kubernetes Deployment -
`kubectl create deploy node-app --image imambo
/node-service:v1`

`kubectl expose deploy node-app --name node-service --port 5000 --type ClusterIP`

`curl node-service-ip:5000/plusone/99`
