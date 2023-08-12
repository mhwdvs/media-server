# media-server Helm Chart

A helm chart (aka Truenas SCALE application) for installing and configuring all of the containers required for a good media server setup. 

## Development

Truenas SCALE runs its apps on `k3s`. For development, the difference between `k3s` and Kubernetes that `k3s` comes with batteries included: Ingress controller, NetworkPolicy controller, LoadBalancer controller. This chart uses NetworkPolicies, so using the same NetworkPolicy controller implemention in both development and production is ideal. To this end, I recommend using `k3d` as your development cluster rather than `minikube` - `minikube` requires you to pick a CNI to provide a NetworkPolicy controller, which I've found 

### Pre-requisites

Install;
- Kubernetes CLI
- K3d
- Helm CLI

### Run

- Start docker engine
- `k3d cluster create localk8s`
- `helm install media-server .`

### Access services

When running with minikube locally, you need to use the `minikube service` command to expose your service to `localhost`

- Get service/s
    `kubectl get svc`
- `minikube service <service name>`

## Implementation

### Resolving pod IP addresses

- With no services: `http://<pod-name>.<namespace>.svc.cluster.local`
- With services: `http://pod-b-service`, where 'pod-b-service' is the name of the target service
