# Kubernetes
Sample Kubernetes Project

### install Chocolatey and kubernetes-cli using instructions found in below link
https://kubernetes.io/docs/tasks/tools/install-kubectl-windows/

# install kustomize
```
curl -s "https://raw.githubusercontent.com/kubernetes-sigs/kustomize/master/hack/install_kustomize.sh"  | bash
sudo mv kustomize /usr/local/bin
```

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
### docker compose
```
docker-compose up -d --build
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
### delete all in current namespace
```
kubectl delete all --all --all-namespaces
kubectl delete daemonsets,replicasets,services,deployments,pods,rc,ingress --all --all-namespaces
```

# Volumes - pod/node dependant
emptyDir - data is stored on the pod, good for 1 pod projects
hostPath - data is stored on the host/node, good for 1 node projects
csi(container storage interface) - can be extended to different cloud provided storage

# Persistent Volumes - pod and node independant
Will not go down when node goes down
Requires Persistent Volume Claim -> This will ensure config of volume does not need to be repeated for each pod
Comparison:
Volume is useful for single node projects
Persistent Volume & Persistent Volume Claim is useful for multi node projects

# ConfigMaps - used to store config data









