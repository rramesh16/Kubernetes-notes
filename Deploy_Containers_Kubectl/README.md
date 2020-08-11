# Deploy Container with Kubectl

## Step 1 - Launch cluster
`minikube start --wait=false`
`kubectl get nodes`

## Step 2 - Kubectl Run
- The `run` command creates a deployment based on the parameters specified
- The deployment is issued to Kubernetes master which launches the Pods and containers required.
- `kubectl run` is similar to `docker run` but at a cluster level

`kubectl run <name of deployment> <properties>`

- To view the kubectl status of deployment
`kubectl get deployments <name of deployment>`

- To view description of the deployment process and/or to find any issues with deployment
`kubectl describe deployment <name of deployment>`

## Step 3 - Kubectl Expose

- Once the deployment is created, use kubectl to create a service which exposes the Pods on a particular port
`kubectl expose deployment <name of deployment> --external-ip="" --port=<host_port no.> --target-port=<container_port no.>`

- Ping the host and see result
`curl http://<ip>:<host_port>`

- To deploy and expose in a single command
`kubectl run <name of deployment>exposed <properties> <port> <hostport>`

- To see the service list
`docker ps | grep <name of deployment>exposed`

## Step 5 - Scale containers
`kubectl scale --replicas=<number> deployment <name of deployment>`

- To see the running replicas
`kubectl get pods`

- To view the endpoint and associated Pods:
`kubectl describe svc <name of deployment`
