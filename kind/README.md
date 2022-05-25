# kind use cases

Every file in this directory indicates one use case for kind.

You can choose one specific file with kind to create cluster as you want, the command will be 

```
kind create cluster --config <config-file>
```

# use cases

## create cluster for specific kubernetes version

doc: https://kind.sigs.k8s.io/docs/user/configuration/#kubernetes-version

You can create a cluster with specific version k8s by parameters in cli

```
kind create cluster --image=kindest/node:v1.20.7
```




