# Deployments & Rollouts in K8s

**Objective**

**This lab demonstrates how to:**
- Deploy an application using a Deployment
- Update the container image
- Observe the rolling update
- Perform a rollback if the new version fails
- This helps understand how Kubernetes manages zero-downtime deployments.

**Step 1 — Create a Deployment**

Deploy an Nginx application with 3 replicas.

```bash
kubectl create deployment naman-nginx-demo --image=nginx:1.21 --replicas=3
```

Verify deployment:
```bash
kubectl get deployments
```

Check pods:
Verify deployment:
```bash
kubectl get pods
```






