# Kubernetes Deployment Templates

[Kubernetes Install Guide](https://github.com/fed51/contrail-kubernetes-docs/blob/master/install/kubernetes/install-kubernetes.md)
[Deploy on Standalone Kubernetes (CentOS)](https://github.com/fed51/contrail-kubernetes-docs/blob/master/install/kubernetes/standalone-kubernetes-centos.md)
[Deploy on Standalone Kubernetes (Ubuntu)](https://github.com/fed51/contrail-kubernetes-docs/blob/master/install/kubernetes/standalone-kubernetes-ubuntu.md)

## v1.17 Patch

To apply the patchs, simply run the following commands:

CentOS:
```
$ patch -b < contrail-single-step-cni-install-centos.patch
```


Ubuntu:
```
$ patch -b < contrail-single-step-cni-install-ubuntu.patch
```


