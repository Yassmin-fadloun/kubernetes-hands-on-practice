# Kubernetes Labels and Selectors

## Objective

Create 4 Pods each with specific labels and then filter and view them using `kubectl` commands.

## Steps and Commands
### 1. Create labeled pods from a [labels.yml](./labels.yml)
```bash
nano labels.yml
```
### 2. Apply the manifest

```bash
kubectl apply -f labels.yml
```
![Logs Result](Result.png)

### 3. Show all labels for all pods

```bash
kubectl get pods --show-labels
```
![Logs Result](Result.png)
### 4. Display specific label column (component)
```bash
kubectl get pods -L app.kubernetes.io/component
```
![Logs Result](Result.png)
### 2. Filter pods by label selector
```bash
kubectl get pods --selector="app.kubernetes.io/component=service"
```
![Logs Result](Result.png)
