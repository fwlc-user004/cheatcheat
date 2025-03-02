# ☸️ Kubernetes Cheatsheet

## 🔹 Installation & Setup
```sh
# Install Kubernetes (kubectl CLI)
sudo apt install kubectl  # Ubuntu/Debian
brew install kubectl      # macOS

# Verify installation
kubectl version --client
```

## 🔹 Kubernetes Cluster Management
```sh
# Check cluster info
kubectl cluster-info

# Get nodes in the cluster
kubectl get nodes

# Get current namespace
kubectl config view --minify | grep namespace
```

## 🔹 Working with Pods
```sh
# List all running pods
kubectl get pods

# Get detailed information about a pod
kubectl describe pod pod_name

# Delete a pod
kubectl delete pod pod_name
```

## 🔹 Working with Deployments
```sh
# Create a deployment
kubectl create deployment nginx-deployment --image=nginx

# List deployments
kubectl get deployments

# Scale a deployment to 3 replicas
kubectl scale deployment nginx-deployment --replicas=3

# Delete a deployment
kubectl delete deployment nginx-deployment
```

## 🔹 Working with Services
```sh
# List services
kubectl get services

# Expose a deployment as a service
kubectl expose deployment nginx-deployment --type=LoadBalancer --port=80
```

## 🔹 ConfigMaps & Secrets
```sh
# Create a ConfigMap
kubectl create configmap my-config --from-literal=key1=value1

# Get ConfigMaps
kubectl get configmaps

# Create a Secret
kubectl create secret generic my-secret --from-literal=password=secretpass
```

## 🔹 Debugging & Logs
```sh
# Get logs of a pod
kubectl logs pod_name

# Execute a command inside a pod
kubectl exec -it pod_name -- /bin/sh
```

## 🔹 Kubernetes Best Practices
- Use **Namespaces** to organize workloads.
- Implement **RBAC (Role-Based Access Control)** for security.
- Prefer **ConfigMaps & Secrets** instead of hardcoded values.
- Use **Horizontal Pod Autoscaling (HPA)** for scalability.
- Monitor cluster health with **Prometheus & Grafana**.

---