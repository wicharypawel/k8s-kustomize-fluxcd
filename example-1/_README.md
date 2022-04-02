# Example 1

## Intro

Example shows how to use kustomize to patch K8s configuration. We will use service definition and update selector using patch.

## Commands

__Run kustomize__
```
kustomize build
```

__Apply to cluster__
```
kustomize build | kubectl apply -f -
```

__Cleanup__
```
kustomize build | kubectl delete -f -
```