# 🧱 K8s-Project

This repository contains three Spring Boot microservices—**Shopfront**, **StockManager**, and **ProductCatalogue**—containerized using Docker and deployed to Kubernetes using `kubectl`. Each service is individually built, packaged, and deployed with its own configuration.

---

## 📦 Applications

- `shopfront` – User-facing storefront service
- `stockmanager` – Inventory management backend
- `productcatalogue` – Product data and catalog service

---

## 🛠️ Tech Stack

- Java + Spring Boot  
- Maven for build management  
- Docker for containerization  
- Kubernetes (via `kubectl`)  
- Docker Hub for image registry  

---

## 🚀 Build and Push Steps

### 1. Build the JAR files (skip tests)

```bash
cd <app-name>
mvn clean install -DskipTests
```

### 2. Build Docker images

```bash
docker build -t manikandan29/<app-name>:latest .
```

### 3. Push to Docker Hub

```bash
docker push manikandan29/<app-name>:latest
```

Repeat the above for each of the three apps: `shopfront`, `productcatalogue`, `stockmanager`.

---

## 📦 Kubernetes Deployment

### 1. Apply service & deployment files

```bash
kubectl apply -f services/shopfront-service.yml
kubectl apply -f services/productcatalogue-service.yml
kubectl apply -f services/stockmanager-service.yml
```

### 2. Use Kubernetes Dashboard

Launch dashboard:

```bash
/usr/local/bin/minikube dashboard
```

Then navigate to:

```
http://<EC2 IP>:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/
```

---

## 🌐 Port Forwarding (for local testing)

| Application        | Container Port | Local Port | Command                            |
|--------------------|----------------|------------|-------------------------------------|
| Shopfront          | 8010           | 8080       | `kubectl port-forward svc/shopfront 8080:8010` |
| Product Catalogue  | 8020           | 8009       | `kubectl port-forward svc/productcatalogue 8009:8020` |
| Stock Manager      | 8030           | 9008       | `kubectl port-forward svc/stockmanager 9008:8030` |

---


```

