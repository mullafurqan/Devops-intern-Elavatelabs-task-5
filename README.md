# 🚀 TASK 5: Kubernetes With Minikube

## Objective
Deploy and manage applications using Kubernetes locally.

---

## ✅ Prerequisites Installation (Windows)

### 1️⃣ Install Minikube
Download Minikube EXE using browser from:
https://storage.googleapis.com/minikube/releases/latest/minikube-installer.exe

Move downloaded file to:
```
C:\Windows\System32
```

Verify:
```
minikube version
```

### 2️⃣ Start Minikube Cluster
```
minikube start --driver=docker
minikube status
kubectl version --client
```

---

## 🏗 Create Kubernetes Deployment & Service

### Create deployment.yaml
```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: hello-deployment
spec:
  replicas: 1
  selector:
    matchLabels:
      app: hello-app
  template:
    metadata:
      labels:
        app: hello-app
    spec:
      containers:
      - name: hello-container
        image: nginx
        ports:
        - containerPort: 80
```

### Create service.yaml
```
apiVersion: v1
kind: Service
metadata:
  name: hello-service
spec:
  type: NodePort
  selector:
    app: hello-app
  ports:
    - port: 80
      targetPort: 80
      nodePort: 30080
```

---

## 🚀 Deploy Into Cluster

```
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
```

---

## ✅ Verification Commands

Check pods:
```
kubectl get pods
```

Check deployments:
```
kubectl get deployments
```

Check services:
```
kubectl get svc
```

Describe pod:
```
kubectl describe pod <pod-name>
```

Logs:
```
kubectl logs <pod-name>
```

---

## 🌍 Access Application In Browser

Enable Minikube tunnel:
```
minikube service hello-service
```

Or directly open:
```
minikube service hello-service --url
```

---

## 📈 Scaling Deployment

```
kubectl scale deployment hello-deployment --replicas=3
kubectl get pods
```

---

## 📸 Deliverables

Take screenshots of:
1. `kubectl get pods`
2. `kubectl get svc`
3. Browser showing NGINX welcome page

---

## 🧹 Clean Up

```
kubectl delete -f deployment.yaml
kubectl delete -f service.yaml
minikube stop
```

---

✅ Task Completed. Congratulations! You are now a Kubernetes Explorer.
