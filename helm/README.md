# media-server Helm Chart

## Local development

### Pre-requisites

Install;
- Kubernetes CLI
- Minikube
- Helm CLI

### Run

- Start docker engine
- `minikube start --cni calico`
    - The cluster should have a CNI that supports NetworkPolicy
- `helm install media-server .`

### Access services

When running with minikube locally, you need to use the `minikube service` command to expose your service to `localhost`

- Get service/s
    `kubectl get svc`
- `minikube service <service name>`