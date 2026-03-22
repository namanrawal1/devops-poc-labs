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

<img width="1121" height="577" alt="image" src="https://github.com/user-attachments/assets/e75b41f1-c7e0-4755-8061-fc3e561718ed" />


Deploy:

```bash
kubectl apply -f green-deployment.yaml
```

Check:
```bash
kubectl get pods --show-labels
```
<img width="1347" height="174" alt="image" src="https://github.com/user-attachments/assets/dfe8ddd8-1b39-4b05-9a7e-b9103fc08bec" />


Now both environments exist:

- Blue (production)
- Green (new version)

But **traffic still goes to Blue**.

---

# Step 4: Switch Traffic to Green

Edit the service:
```bash
kubectl edit svc demo-service
```


Change selector from:
version: blue


to:
version: green

<img width="1050" height="674" alt="image" src="https://github.com/user-attachments/assets/eadbff94-3245-4c41-8765-3815a365233f" />


Save the file.

Traffic will instantly switch to **Green pods**.

---

# Step 5: Verify Deployment

Check running pods:


Save the file.

Traffic will instantly switch to **Green pods**.

---

# Step 5: Verify Deployment

Check running pods:
```bash
kubectl get pods
```


Check service routing:
```bash
kubectl describe svc demo-service
```


Users now receive traffic from **Green version**.

<img width="1540" height="659" alt="image" src="https://github.com/user-attachments/assets/321fef3b-715c-4908-9a98-39fdb3687423" />

---

# Rollback Strategy

If issues occur, switch traffic back to Blue:
```bash
kubectl edit svc demo-service
```


Change:
version: green

back to
version: blue


This allows **instant rollback with zero downtime**.

---

# Benefits of Blue-Green Deployment

- Zero downtime releases
- Easy rollback
- Safe production testing
- Reduced deployment risk




