# show all cluster in k'8
kubectl get nodes 

kubectl get pods -n namespace -o wide

kubectl get all --all

kubectl exec -it <name of pod> <shell type /bin/bash>

kubectl api-resources

# check pods in the kube system control plane
kubectl get pods -n kube-system

# find security issues with yamls kubernetes resource
snyk iac test deployment.yaml 