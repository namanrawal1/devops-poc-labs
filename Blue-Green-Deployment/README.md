# Blue-Green Deployment Example (Kubernetes)

This project demonstrates a **Blue-Green Deployment strategy** using Kubernetes to achieve **zero-downtime deployments**.

Blue-Green deployment allows you to run two versions of an application simultaneously and switch traffic between them safely.

---

# Architecture

```bash
Users
│
▼
Kubernetes Service
│
├── Blue Pods (v1 - Current Production)
└── Green Pods (v2 - New Version)
```


- **Blue Environment** → Current production version
- **Green Environment** → New version for testing
- Traffic is switched by updating the **Service selector**

---

# Prerequisites

- Kubernetes Cluster
- kubectl installed
- Basic knowledge of Kubernetes objects

Verify access:
```bash
kubectl get nodes
```


---

# Step 1: Deploy Blue Version

Create the file:

`blue-deployment.yaml`


<img width="1080" height="654" alt="image" src="https://github.com/user-attachments/assets/b05e93d1-898d-4f07-9f59-48ebeac814be" />


Apply deployment:
```bash
kubectl apply -f blue-deployment.yaml
```

Verify:
```bash
kubectl get pods
```


---

# Step 2: Create Service

The service routes traffic to **Blue pods** initially.

Create:

`service.yaml`

<img width="963" height="374" alt="image" src="https://github.com/user-attachments/assets/bc93e994-96e7-4b00-a2be-40801b517cd8" />


Apply:
```bash
kubectl apply -f service.yaml
```


Check service:
```bash
kubectl get svc
```


Traffic now goes to **Blue deployment**.

---

# Step 3: Deploy Green Version

Create:

`green-deployment.yaml`

