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

# create deployment
kubectl create deployment --dry-run=client --image locahost:5000/explorecalifornia.com --output=yaml > deployment.yaml

# deploy the yaml file
kubectl apply -f deployment.yaml

# port forwarding in case load balancer or ingress is not available
kubectl port-forward <deploymen/serviuce> <oustide-port>:<inside-port>
kubectl port-forward deployment/expolorecalifornia.com 8080:80

# Genrate service.yaml 
kubectl create service clusterip --dry-run=client --tcp=80:80 explorecalifornia.com --output=yaml > service.yaml

# Ingress is load balancer with routing rules ==> used more like an interface for AWS micrsoft and other cloud provided Load balancer
kubcectl create ingress <name> --rule="foo.com/path*=<service-name>:<port>, tls=<cret-name> 

kubectl create ingress explorcalifornia.com --rule="explorecalifornia.com/=explorecalifornia-svc:80,tls=my-cert" 

kubectl create ingress explorcalifornia.com --rule="explorecalifornia.com/=explorecalifornia-svc:80" --dry-run=client --output=yaml > ingress.yaml

# In make file INGRESS is being added while creating cluster under kind_config.yaml (creating kubernetes cluster)
# add below lines under nodes and under InitConfiguration make ingress-ready=true
nodes:
- role: control-plane
  kubeadmConfigPatches:
  - |
    kind: InitConfiguration
    nodeRegistration:
      kubeletExtraArgs:
        node-labels: "ingress-ready=true"