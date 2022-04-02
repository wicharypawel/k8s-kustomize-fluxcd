# Example 2

## Intro

Example shows how to use kustomize to merge multiple files containing kubernetes configuration. We can use Kustomize to apply namespace to multiple files.

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