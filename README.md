# 3 Tier Kubernetes Project
This is a 3 Tier Kubernetes Project

## 3 Tier
1. Python Notes App
2. Nginx
3. Flask App with MySQL database

## Installation
1. Clone the repository
```
git clone https://github.com/12345ujjwal/dual-service-k8s-project/
```

2. Get inside the directory
```
cd dual-service-k8s-project/k8s
```
3. Create a KIND cluster
```
kind create cluster --name project --config=kind-cluster.yml
```

3. Apply the YML for Python Nodes app
```
kubectl apply -f deployment.yml
kubectl apply -f service.yml
```

## Nginx

Install Nginx reverse proxy to make this application available

`sudo apt-get update`
`sudo apt install nginx`
