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
4. Install ingress-controller and apply ingress YAML

- Installing Ingress controller
```
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/kind/deploy.yaml
```

- Verify the installation
```
kubectl get pods -n ingress-nginx
```

## Service-1: Apply the YML for Python Nodes app
```
kubectl apply -f deployment.yml
kubectl apply -f service.yml
```

## Service-2: Apply the YML for Nginx
In root project directory, run the below commands
1. Change directory to Nginx
```
cd nginx/
```
2. Apply all YAML files for Nginx
```
kubectl apply -f deployment.yml
kubectl apply -f service.yml
```
If you want to use persistent volume instead, apply the pv.yml , pvc.yml and vol-deployment.yml

## Service-3: Flask App with MySQL Database
In root project directory, run the below commands
1. Change directory to Docker-2_tier_flask_app
```
cd Docker-2_tier_flask_app/k8s
```
2. Apply all YAML files for Flask and MySQL 
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

## Ingress apply and controller port forward
Run the below command in Project Root directory
```
kubectl apply -f ingress.yml
kubectl port-forward svc/ingress-nginx-controller -n ingress-nginx 8000:80 --address=0.0.0.0
```

## Adminer installation and port forwarding

```
kubectl run adminer --image=adminer --port=8080
kubectl expose pod adminer --type=NodePort --port=8080
```
```
kubectl get svc adminer
```
```
kubectl port-forward svc/adminer 8080:8080
```
test credential:
Server: mydb <br>
username: admin <br>
Password: admin

## Screenshot
- Service 1
<img width="1137" height="973" alt="image" src="https://github.com/user-attachments/assets/d2505fe1-92cc-4cba-aa65-63bfc393872d" />

- Service 2
<img width="981" height="416" alt="image" src="https://github.com/user-attachments/assets/f545a506-7b91-4c5b-9f96-db28de3de385" />

- Service 3
<img width="1137" height="973" alt="image" src="https://github.com/user-attachments/assets/7624605a-0a40-48ee-bdc8-4e57919eb2eb" />

- Adminer
<img width="1044" height="750" alt="image" src="https://github.com/user-attachments/assets/762d1c97-8e59-4d66-ac66-dc11ccc82db5" />

