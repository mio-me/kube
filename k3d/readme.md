# K3d Guide

# Create
```
k3d cluster create --api-port 6550 -p "8081:80@loadbalancer" --agents 2 --registry-config "/path/to/registries.yml" my-cluster
```

https://k3d.io/v5.2.0/usage

# Todo

- [] nextcloud tls ingress
