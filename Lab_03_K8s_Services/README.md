# ClusterIP and NodePort Services

This lab demonstrates the use of Kubernetes Services: `ClusterIP` for internal access and `NodePort` for external access. It also covers how to expose services, use curl within a pod, and test service reachability.

---
## Objective

- Create two Nginx pods with labels.
- Modify the HTML response of each pod.
- Create and test a ClusterIP service.
- Test the service using a third Ubuntu pod with `curl`.
- Use port-forwarding to test access from your local machine.
- Create and test a NodePort service.

---

## Steps and Commands

### 1. Create the Nginx [pods.yml](./pods.yml)
```bash
nano pods.yaml
```
### 2. Apply the Pod
```bash
kubectl apply -f pod.yml
```
### 3.  Verify the Pod is Running
```bash
kubectl get pods
```
### 4. Modify index.html in each pod to display unique identity
```bash
kubectl exec -it web-app01 -- bash
apt update && apt install -y vim
vim /usr/share/nginx/html/index.html
# nginx! ------> app01
exit

kubectl exec -it web-app02 -- bash
apt update && apt install -y vim
vim /usr/share/nginx/html/index.html
# nginx! ------> app02
exit

```
### 5.  Create a ClusterIP service [clusterip-service.yaml](./clusterip-service.yaml)
```bash
nano clusterip-service.yaml
```
### 6. Apply and verify:
```bash
kubectl apply -f clusterip-service.yaml
kubectl get svc
```
![Logs Result](Result.png)
### 7. Test using a third Ubuntu pod
```bash
kubectl run ubuntu --image=ubuntu -it --rm -- /bin/bash
apt update
apt install -y curl
curl my-clusterip-service.default.svc.cluster.local
curl my-clusterip-service
exit
```
![Logs Result](Result.png)
### 8. Port-forward the service
```bash
kubectl port-forward service/my-clusterip-service 8080:80
```
![Logs Result](Result.png)
### 9. Create NodePort service [nodeport-service.yaml](./nodeport-service.yaml)
```bash
nano nodeport-service.yaml
```
### 10. Apply and verify:
```bash
kubectl apply -f nodeport-service.yaml
kubectl get svc
```
![Logs Result](Result.png)
