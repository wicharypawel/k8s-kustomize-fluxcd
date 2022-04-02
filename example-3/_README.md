# Example 3

## Intro

Example shows how to use kustomize to patch configuration.

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