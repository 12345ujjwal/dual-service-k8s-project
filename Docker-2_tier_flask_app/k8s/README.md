# How to setup two-tier application deployment on kubernetes cluster
## First setup kubernetes KIND cluster
Use this repository to setup your flask application and MYSQL in your Kubernetes Project

## SetUp
- First clone the code to your machine and switch to 3-tier branch
```bash
git clone https://github.com/12345ujjwal/dual-service-k8s-project/
cd dual-service-k8s-project/Docker-2_tier_flask_app
```
- Now, execute below commands one by one
```bash
kubectl apply -f twotier-deployment.yml
```
```bash
kubectl apply -f twotier-deployment-svc.yml
```
```bash
kubectl apply -f persistent-volume.yml
```
```bash
kubectl apply -f persistent-volume-claim.yml
```
```bash
kubectl apply -f mysql-deployment.yml
```
```bash
kubectl apply -f mysql-deployment-svc.yml
```

