# kube

## Start Services

```Bash
K3S_TOKEN=${RANDOM}${RANDOM}${RANDOM} docker-compose up --build -d --remove-orphans
```

## Save config
```Bash
cp kubeconfig.yaml ~/.kube/config
```

## Rancher
https://rancher.com/docs/rancher/v2.x/en/installation/install-rancher-on-k8s/
Add helm repo
```Bash
curl https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3 | bash
helm repo add rancher-stable https://releases.rancher.com/server-charts/stable
kubectl create namespace cattle-system
```
Use cert-manager for rancher-generated or Let's Encrypt certificates.
```Bash
kubectl apply --validate=false -f https://github.com/jetstack/cert-manager/releases/download/v1.0.4/cert-manager.crds.yaml
kubectl create namespace cert-manager
helm repo add jetstack https://charts.jetstack.io
helm repo update
helm install \
  cert-manager jetstack/cert-manager \
  --namespace cert-manager \
  --version v1.0.4
```
Add a DNS entry pointing at your load balancer.
Install Rancher. Set the hostname to the DNS name you pointed at your load balancer and adjust replicas accordingly.
```Bash
helm install rancher rancher-stable/rancher \
  --namespace cattle-system \
  --set hostname=rancher.my.org \
  --set replicas=1
```

## MetalLB
https://metallb.universe.tf/installation/
````
kustomize build config/metallb | kubectl apply -f -
```

## Resources
https://rancher.com/docs/k3s/latest/en/advanced/#running-k3d-k3s-in-docker-and-docker-compose
https://github.com/rancher/k3d
https://github.com/k3s-io/k3s/blob/master/docker-compose.yml
https://rancher.com/docs/rancher/v2.x/en/installation/resources/k8s-tutorials/infrastructure-tutorials/infra-for-ha-with-external-db/