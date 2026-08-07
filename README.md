# 2 Tier Kubernetes Project
This is a 2 Tier Kubernetes Project. If you want to 3 Tier project, switch to branch 3-tier

## 2 Tier
1. Python Notes App
2. Nginx

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

## Service-1: Apply the YML for Python Nodes app
```
kubectl apply -f namespace.yml
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

3. Install ingress-controller and apply ingress YAML

- Installing Ingress controller
```
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/kind/deploy.yaml
```

- Verify the installation
```
kubectl get pods -n ingress-nginx
```

- Apply the ingress file
```
kubectl apply -f ingress.yml
```

## Ingress controller port forward
```
kubectl port-forward svc/ingress-nginx-controller -n ingress-nginx 8000:80 --address=0.0.0.0
```

## Screenshot
- Service 1
<img width="1137" height="973" alt="image" src="https://github.com/user-attachments/assets/d2505fe1-92cc-4cba-aa65-63bfc393872d" />

- Service 2
<img width="981" height="416" alt="image" src="https://github.com/user-attachments/assets/f545a506-7b91-4c5b-9f96-db28de3de385" />
