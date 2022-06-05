# pod-validatingwebhook
This is simplest webhook for Pod validation built by [Kubebuilder](https://github.com/kubernetes-sigs/kubebuilder)

Just a reminder for some configuration

1. Provide the mirrored images
    * config/default/manager_auth_proxy_patch.yaml
    * Dockerfile
2. Add builder.go to resolve the issue for https://github.com/kubernetes-sigs/controller-runtime/issues/1670
3. Modify kustomization config to disable crd  and enable webhook and cert-manager
	* config/default/kustomization.yaml
4. Add ClusterRole for RBAC
	* config/rbac/role.yaml
5. Update IMG variable in Makefile

## Description
// TODO(user): An in-depth paragraph about your project and overview of use

## Getting Started
You’ll need a Kubernetes cluster to run against. You can use [KIND](https://sigs.k8s.io/kind) to get a local cluster for testing, or run against a remote cluster.
**Note:** Your controller will automatically use the current context in your kubeconfig file (i.e. whatever cluster `kubectl cluster-info` shows).

### Running on the cluster
1. Install Instances of Custom Resources:

```sh
kubectl apply -f config/samples/
```

2. Build and push your image to the location specified by `IMG`:
	
```sh
make docker-build docker-push IMG=<some-registry>/pod-validatingwebhook:tag
```
	
3. Deploy the controller to the cluster with the image specified by `IMG`:

```sh
make deploy IMG=<some-registry>/pod-validatingwebhook:tag
```

### Uninstall CRDs
To delete the CRDs from the cluster:

```sh
make uninstall
```

### Undeploy controller
UnDeploy the controller to the cluster:

```sh
make undeploy
```

## Contributing
// TODO(user): Add detailed information on how you would like others to contribute to this project

### How it works
This project aims to follow the Kubernetes [Operator pattern](https://kubernetes.io/docs/concepts/extend-kubernetes/operator/)

It uses [Controllers](https://kubernetes.io/docs/concepts/architecture/controller/) 
which provides a reconcile function responsible for synchronizing resources untile the desired state is reached on the cluster 

### Test It Out
1. Install the CRDs into the cluster:

```sh
make install
```

2. Run your controller (this will run in the foreground, so switch to a new terminal if you want to leave it running):

```sh
make run
```

**NOTE:** You can also run this in one step by running: `make install run`

### Modifying the API definitions
If you are editing the API definitions, generate the manifests such as CRs or CRDs using:

```sh
make manifests
```

**NOTE:** Run `make --help` for more information on all potential `make` targets

More information can be found via the [Kubebuilder Documentation](https://book.kubebuilder.io/introduction.html)

## License

Copyright 2022 denverdino@gmail.com.

## Reference

https://medium.com/trendyol-tech/getting-started-to-write-your-first-kubernetes-admission-webhook-part-2-48d0b0b1780e