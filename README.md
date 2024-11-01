# Hello Go Config
GitOps Config project for the hello-go project.

## Prerequisite
1. OpenShift 4.14+ cluster with admin access
2. OpenShift GitOps 1.14.x+

## Setup

```shell
oc new-project hello-go
oc label namespace hello-go argocd.argoproj.io/managed-by=openshift-gitops
oc policy add-role-to-user system:image-puller system:serviceaccount:hello-go:default -n hello-cicd
oc apply -f ./application.yaml
```

## Testing

```shell
curl --head https://$(oc get routes/hello-go -n hello-go -o jsonpath="{.spec.host}")
```
