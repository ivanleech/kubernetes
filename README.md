# Kubernetes
Sample Kubernetes Project

### install Chocolatey and kubernetes-cli using instructions found in below link
https://kubernetes.io/docs/tasks/tools/install-kubectl-windows/

# DockerHub - build image and push to dockerhub 
```
docker build -t kube-first-app .
docker tag -t kube-first-app <dockerhub_username>/kube-first-app 
docker push <dockerhub_username>/kube-first-app
```
### build and tag in one step
```
docker build -t <dockerhub_username>/kube-data-demo .
docker push <dockerhub_username>/kube-data-demo
```

# Minikube - required to start kubernetes locally
```
minikube start
minikube status
minikube dashboard
```

# Kubectl - required to interact with kubernetes
```
kubectl apply -f master-deployment.yaml
```
### rollback 1 deployment
```
kubectl rollout undo deployment
```
### check history and choose version to rollback to
```
kubectl rollout history deployment/second-app-deployment
kubectl rollout history deployment/second-app-deployment --revision=4
kubectl rollout undo deployment/second-app-deployment --to-revision=4
```

# Volumes - data survives container restarts but not pod restarts
emptyDir - data is stored on the pod, good for 1 pod projects
hostPath - data is stored on the host/node, good for 1 node projects
csi(container storage interface) - can be extended to different cloud provided storage

# Persistent Volumes - pod and node independant





