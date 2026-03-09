Kubernetes Self-Healing Use-case 

This demo shows the self-healing capability of Kubernetes. In a Kubernetes cluster, controllers continuously monitor the desired state of applications. If a pod fails or is deleted, Kubernetes automatically recreates it to maintain the desired number of replicas. 

 

Step 1 – Create deployment 

We create a deployment named nginx-demo using the nginx container image with three replicas. This ensures Kubernetes maintains three running pods for the application. 

 

# kubectl create deployment nginx-demo --image=nginx --replicas=3 

 

Check pods in default namespace : # kubectl get pods 

 

 

 

 

 

 

 

Step 2 – Delete a pod 

Next, we manually delete one of the running pods. Kubernetes detects that the number of replicas has dropped below the desired state and automatically creates a new pod to replace the deleted one. 

 

 

Now check pods again: kubectl get pods  

You will see Kubernetes create a new pod automatically. 

 

“Kubernetes Self-Healing: How Pods Automatically Recover from Failure” 

 

Conclusion: This experiment demonstrates Kubernetes' self-healing features. When a pod fails or is deleted, the deployment controller automatically recreates it to maintain application's availability and Stability. 

 
