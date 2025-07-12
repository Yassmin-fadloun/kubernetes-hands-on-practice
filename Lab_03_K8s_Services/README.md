# Lab 03: ClusterIP and NodePort Services

This lab demonstrates the use of Kubernetes Services: `ClusterIP` for internal access and `NodePort` for external access. It also covers how to expose services, use curl within a pod, and test service reachability.

---

## 🧪 Task Description

- Create two Nginx pods with labels.
- Modify the HTML response of each pod.
- Create and test a ClusterIP service.
- Test the service using a third Ubuntu pod with `curl`.
- Use port-forwarding to test access from your local machine.
- Create and test a NodePort service.

---

## 🧾 Step-by-Step Instructions

### 🟢 Step 1: Create the Nginx pods

```bash
nano pods.yaml
