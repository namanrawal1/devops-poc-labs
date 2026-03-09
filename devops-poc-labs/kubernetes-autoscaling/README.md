# Kubernetes Self-Healing

## Overview

This demo shows the **self-healing capability of Kubernetes**.

In a Kubernetes cluster, controllers continuously monitor the **desired state** of applications.  
If a **pod fails or is deleted**, Kubernetes automatically recreates it to maintain the desired number of replicas.

---

## Step 1 – Create a Deployment

Create a deployment named **nginx-demo** using the nginx container image with **3 replicas**.

```bash
kubectl create deployment nginx-demo --image=nginx --replicas=3
```

<img width="625" height="38" alt="image" src="https://github.com/user-attachments/assets/8f886ee2-e403-48b7-a7d5-b2b16a078d5e" />



Check pods in default namespace : 

```bash
kubectl get pods
```

<img width="618" height="126" alt="image" src="https://github.com/user-attachments/assets/929cc3b9-10fc-4e49-a946-da2f9283f50e" />

## Step 2 – Delete a pod 


Next, we manually delete one of the running pods. Kubernetes detects that the number of replicas has dropped below the desired state and automatically creates a new pod to replace the deleted one. 


<img width="623" height="65" alt="image" src="https://github.com/user-attachments/assets/a9b2b491-3c9e-4dbf-9a01-823ce03c5209" />


Now check pods again: 

```bash
kubectl get pods
```


You will see Kubernetes create a new pod automatically. 

<img width="573" height="97" alt="image" src="https://github.com/user-attachments/assets/64d09043-83b8-4637-8db7-984701c3a77d" />

“Kubernetes Self-Healing: How Pods Automatically Recover from Failure” 

Conclusion: This experiment demonstrates Kubernetes' self-healing features. When a pod fails or is deleted, the deployment controller automatically recreates it to maintain application's availability and Stability. 

