# Kubernetes Persistent Volumes Lab 🚀

## 📌 Overview

In this lab, I explored how Kubernetes handles **persistent storage** using:

- PersistentVolume (PV)
- PersistentVolumeClaim (PVC)
- Pod volume mounts

I also validated **data persistence across pod restarts** and explored **NodePort networking behavior**.

---

## 🎯 Objectives

- Create a Persistent Volume (PV)
- Create a Persistent Volume Claim (PVC)
- Mount storage to a Pod
- Write and verify data persistence
- Expose the application using a Service
- Data persistence across pod recreation

---

## 🧱 Architecture

User → NodeIP:NodePort → Service → Pod → PVC → PV → Disk

## Steps

Step 1 — Create Persistent Volume (PV)
A Persistent Volume (PV) represents a piece of storage in the cluster. Here we create a local storage backed by the node using hostPath.

<img width="788" height="271" alt="image" src="https://github.com/user-attachments/assets/eb9c791e-967e-4e73-99c5-d575384bbda4" />

Step 2 — Create Persistent Volume Claim (PVC)
A PVC is a request for storage by a user. It binds to an available PV and abstracts the underlying storage from the application.

<img width="635" height="217" alt="image" src="https://github.com/user-attachments/assets/8d2d6c5d-aab5-4c05-880a-b31315bc4a29" />

Step 3 — Create Pod with Volume Mount
We deploy a pod and mount the PVC inside the container so the application can read/write data to persistent storage.

<img width="627" height="329" alt="image" src="https://github.com/user-attachments/assets/7f043d13-e8c2-407e-875e-d67622e747dd" />

Step 4 — Write Data to the Persistent Volume created
We manually write data inside the mounted directory to verify that the storage is working correctly.

<img width="780" height="227" alt="image" src="https://github.com/user-attachments/assets/e902f31b-3c20-4c3d-8834-3be7d5f0ba2d" />

Step 5 — Expose Pod via NodePort
We create a NodePort service to expose the application externally, allowing access via <NodeIP>:NodePort.

<img width="686" height="225" alt="image" src="https://github.com/user-attachments/assets/01ae2a62-81e0-4ce7-9f89-367aa1310d33" />

<img width="1284" height="481" alt="image" src="https://github.com/user-attachments/assets/151a9845-aae8-46ce-8079-11aeeba177f7" />

Step 6 — Test Data Persistence
We delete the pod to simulate failure and recreate it to test whether the data persists across pod lifecycle.

<img width="885" height="276" alt="image" src="https://github.com/user-attachments/assets/d08953e6-ad18-417c-ae9e-89a692bd9a91" />




