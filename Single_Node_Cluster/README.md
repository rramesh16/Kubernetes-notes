# Kubernetes

## Launch Single Node Kubernetes Cluster

### Step 1 - Start Minikube
- Check if Minikube has been installed
`minikube version`
- Start the cluster
`minikube start --wait=false`

### Step 2 - Cluster Info
- Cluster can be interacted with using `kubectl` CLI
- To view details of cluster and its health status
`kubectl cluster-info`
- To view nodes in the cluster
`kubectl get nodes`
- If the node is marked as NotReady then its still starting the components

### Step 3 - Deploy Containers
- Deploy containers onto the Cluster
`kubectl create deployment first-deployment -- image=katacoda/docker-http-server`
- Discover status of deployment via running Pods
`kubectl get pods`
- Expose the container via different networking options. E.g. NodePort which provides dynamic port to a container
`kubectl expose deployment first-deployment --port=80 --type=NodePort`
- Find the allocated port and execute a HTTP request
``export PORT=$(kubectl get svc first-deployment -o go-template='{{range.spec.ports}}{{if .nodePort}}{{.nodePort}}{{"\n"}}{{end}}{{end}}')``
``echo "Accessing host01:$PORT"``
``curl host01:$PORT``

## Step 4 - Dashboard
- To enable dashboard using Minikube
`minikube addons enable dashboard`
- Make the Kubernetes available
`kubectl apply -f /opt/kubernetes-dashboard.yaml`
- Watch the Pods within the kube-system
`kubectl get pods -n kubernetes-dashboard -w`
