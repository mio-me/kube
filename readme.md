# kube

## Start Services

```Bash
K3S_TOKEN=${RANDOM}${RANDOM}${RANDOM} docker-compose up
```

## Save config
```Bash
cp kubeconfig.yaml ~/.kube/config
```

## Resources
https://rancher.com/docs/k3s/latest/en/advanced/#running-k3d-k3s-in-docker-and-docker-compose
https://github.com/rancher/k3d
https://github.com/k3s-io/k3s/blob/master/docker-compose.yml
https://rancher.com/docs/rancher/v2.x/en/installation/resources/k8s-tutorials/infrastructure-tutorials/infra-for-ha-with-external-db/