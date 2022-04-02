# Example 3

## Intro

Example shows how to apply overlay to the base configuration.

## What is an overlay

`https://kubectl.docs.kubernetes.io/references/kustomize/glossary/#overlay`

## Files overview

```
./apps/
├── base
│   └── podinfo
│       ├── kustomization.yaml
│       ├── namespace.yaml
│       └── pod-info-app.yaml
├── production
│   ├── kustomization.yaml
│   └── pod-info-app-patch.yaml
└── staging
    ├── kustomization.yaml
    └── pod-info-app-patch.yaml
```

## Commands

__Run kustomize__
```
kustomize build ./staging
or
kustomize build ./production
```

__Apply to cluster__
```
kustomize build ./staging | kubectl apply -f -
or
kustomize build ./production | kubectl apply -f -
```

__View deployed application__
```
kubectl port-forward svc/pod-info-app 8000:8000 -n example-4
Open http://localhost:8000/ in browser
```

__Cleanup__
```
kubectl delete namespace example-4
```