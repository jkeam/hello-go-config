# Hello Go Config
GitOps Config project for the hello-go project.

## Prerequisite
1. OpenShift 4.14+ cluster with admin access
2. OpenShift GitOps 1.14.x+

## Setup

```shell
oc new-project hello-config
oc label namespace hello-config argocd.argoproj.io/managed-by=openshift-gitops
oc apply -f ./application.yaml
```

## Testing

```shell
curl --head https://$(oc get routes/hello-nginx-route -n hello -o jsonpath="{.spec.host}")
```

## See Changes

Update `base/kustomization.yaml` to change the image tag
to see argocd pick up change and deploy it.
