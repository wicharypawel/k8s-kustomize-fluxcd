# Example 5

## Intro

Example shows how to install and configure FluxCD on cluster

Based on: `https://fluxcd.io/docs/installation/`

## Repository structure

The Git repository contains the following top directories:

- **apps** dir contains application definition with a custom configuration per cluster
- **infrastructure** dir contains common infra tools such as NGINX ingress controller and Helm repository definitions
- **clusters** dir contains the Flux configuration per cluster

```
├── apps
│   ├── base
│   ├── production 
│   └── staging
├── infrastructure
│   ├── nginx (optional)
│   ├── redis (optional)
│   ├── cert-manager (optional)
│   └── sources (optional)
└── clusters
    ├── production
    └── staging
```

Based on: `https://github.com/fluxcd/flux2-kustomize-helm-example/blob/main/README.md`

## Commands

__Configure Flux__
```
flux bootstrap git --url=https://github.com/wicharypawel/k8s-kustomize-fluxcd.git --branch=master --path=example-5/clusters/staging --username=$env:GITHUB_USER --password=$env:GITHUB_TOKEN --token-auth=true
```

__View deployed application__
```
kubectl get all -n example-5
Wait a minute to flux reconcile cluster state with git, retry command
```

__Trigger reconcilliation__
```
flux reconcile source git flux-system
flux reconcile kustomization infrastructure
flux reconcile kustomization apps
```

__Cleanup__
```
flux uninstall --namespace=flux-system
kubectl delete namespace example-5
```

__Note:__ that the uninstall command will not remove any Kubernetes objects or Helm releases that were reconciled on the cluster by Flux. It is safe to uninstall Flux and rerun the boostrap, any existing workloads will not be affected.