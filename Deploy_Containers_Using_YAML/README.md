# Deploy Containers Using yaml

## NOTE: Refer to the .yaml file

## Create Deployment
- Deploy the deployment.yaml file:
`kubectl create -f <file name>`
or
`kubectl apply -f <file name>`

- List all the deployed objects:
`kubectl get deployment`

- Output details of individual deployments:
`kubectl describe deployment <app name>`

## Create Service

- Deploy the service.yaml file:

- Details of all the Service objects deployed
`kubectl get svc`

- Describe the object:
`kubectl  describe svc <name of service>`

- Issuing request to the port
 `curl host01:<nodePort>`

## Scale deployment

- To increase the number of instances running update the `replicas` in deployment.yaml file

- Apply the change
`kubectl apply -f <file name>`

- View the updated cluster
`kubectl get deployment`

- View additional Pods
`kubectl get pods`
