# Kubernetes Deployment Templates

[Kubernetes Install Guide](https://github.com/fed51/contrail-kubernetes-docs/blob/master/install/kubernetes/install-kubernetes.md)

[Deploy on Standalone Kubernetes (CentOS)](https://github.com/fed51/contrail-kubernetes-docs/blob/master/install/kubernetes/standalone-kubernetes-centos.md)

[Deploy on Standalone Kubernetes (Ubuntu)](https://github.com/fed51/contrail-kubernetes-docs/blob/master/install/kubernetes/standalone-kubernetes-ubuntu.md)


## Applying Patch

### Basic

Download the yaml and patch files to apply the patch locally.

Run the following command too apply the patch:

CentOS:
```
$ patch -b < contrail-single-step-cni-install-centos.patch
```

Ubuntu:
```
$ patch -b < contrail-single-step-cni-install-ubuntu.patch
```

## Applying Patch During Deployment

### Contrail
CentOS:
```
K8S_MASTER_IP=x.x.x.x; \
    CONTRAIL_REPO="ci-repo.englab.juniper.net:5010"; \
    CONTRAIL_RELEASE="latest"; \
    mkdir -pm 777 /var/lib/contrail/kafka-logs; \
    TMPLT="https://raw.githubusercontent.com/fed51/contrail-kubernetes-docs/master/install/kubernetes/templates/contrail-single-step-cni-install-centos.yaml"; \
    PATCH="https://raw.githubusercontent.com/fed51/contrail-kubernetes-docs/master/install/kubernetes/templates/contrail-single-step-cni-install-centos.patch"; \
    FILE=$(basename -- "$TMPLT"); \
    curl $TMPLT -o /tmp/${TMPLT##*/}; \
    curl $PATCH -o /tmp/${PATCH##*/}; \
    patch /tmp/$FILE /tmp/${PATCH##*/}; \
    sed -i "s/{{ K8S_MASTER_IP }}/$K8S_MASTER_IP/g; \
        s/{{ CONTRAIL_REPO }}/$CONTRAIL_REPO/g; \
        s/{{ CONTRAIL_RELEASE }}/$CONTRAIL_RELEASE/g" \
        /tmp/$FILE; \
    kubectl apply -f /tmp/$FILE; \
    rm /tmp/${FILE%.*}*
```

Ubuntu:
```
K8S_MASTER_IP=x.x.x.x; \
    CONTRAIL_REPO="ci-repo.englab.juniper.net:5010"; \
    CONTRAIL_RELEASE="latest"; \
    mkdir -pm 777 /var/lib/contrail/kafka-logs; \
    TMPLT="https://raw.githubusercontent.com/fed51/contrail-kubernetes-docs/master/install/kubernetes/templates/contrail-single-step-cni-install-ubuntu.yaml"; \
    PATCH="https://raw.githubusercontent.com/fed51/contrail-kubernetes-docs/master/install/kubernetes/templates/contrail-single-step-cni-install-ubuntu.patch"; \
    FILE=$(basename -- "$URL"); \
    curl $TMPLT -o /tmp/${TMPLT##*/}; \
    curl $PATCH -o /tmp/${PATCH##*/}; \
    patch /tmp/$FILE /tmp/${PATCH##*/}; \
    sed -i "s/{{ K8S_MASTER_IP }}/$K8S_MASTER_IP/g; \
        s/{{ CONTRAIL_REPO }}/$CONTRAIL_REPO/g; \
        s/{{ CONTRAIL_RELEASE }}/$CONTRAIL_RELEASE/g" \
        /var/$FILE; \
    kubectl apply -f /var/$FILE; \
    rm /var/${FILE%.*}*
```

### Tungsten Fabric

CentOS:
```
K8S_MASTER_IP=x.x.x.x; \
    CONTRAIL_REPO="docker.io\/opencontrailnightly"; \
    CONTRAIL_RELEASE="latest"; \
    mkdir -pm 777 /var/lib/contrail/kafka-logs; \
    TMPLT="https://raw.githubusercontent.com/fed51/contrail-kubernetes-docs/master/install/kubernetes/templates/contrail-single-step-cni-install-centos.yaml"; \
    PATCH="https://raw.githubusercontent.com/fed51/contrail-kubernetes-docs/master/install/kubernetes/templates/contrail-single-step-cni-install-centos.patch"; \
    FILE=$(basename -- "$TMPLT"); \
    curl $TMPLT -o /tmp/${TMPLT##*/}; \
    curl $PATCH -o /tmp/${PATCH##*/}; \
    patch /tmp/$FILE /tmp/${PATCH##*/}; \
    sed -i "s/{{ K8S_MASTER_IP }}/$K8S_MASTER_IP/g; \
        s/{{ CONTRAIL_REPO }}/$CONTRAIL_REPO/g; \
        s/{{ CONTRAIL_RELEASE }}/$CONTRAIL_RELEASE/g" \
        /tmp/$FILE; \
    kubectl apply -f /tmp/$FILE; \
    rm /tmp/${FILE%.*}*
```

Ubuntu:
```
K8S_MASTER_IP=x.x.x.x; \
    CONTRAIL_REPO="docker.io\/opencontrailnightly"; \
    CONTRAIL_RELEASE="latest"; \
    mkdir -pm 777 /var/lib/contrail/kafka-logs; \
    TMPLT="https://raw.githubusercontent.com/fed51/contrail-kubernetes-docs/master/install/kubernetes/templates/contrail-single-step-cni-install-ubuntu.yaml"; \
    PATCH="https://raw.githubusercontent.com/fed51/contrail-kubernetes-docs/master/install/kubernetes/templates/contrail-single-step-cni-install-ubuntu.patch"; \
    FILE=$(basename -- "$TMPLT"); \
    curl $TMPLT -o /tmp/${TMPLT##*/}; \
    curl $PATCH -o /tmp/${PATCH##*/}; \
    patch /tmp/$FILE /tmp/${PATCH##*/}; \
    sed -i "s/{{ K8S_MASTER_IP }}/$K8S_MASTER_IP/g; \
        s/{{ CONTRAIL_REPO }}/$CONTRAIL_REPO/g; \
        s/{{ CONTRAIL_RELEASE }}/$CONTRAIL_RELEASE/g" \
        /tmp/$FILE; \
    kubectl apply -f /tmp/$FILE; \
    rm /tmp/${FILE%.*}*
```
