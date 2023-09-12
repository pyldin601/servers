# casa arm64 cluster

## Setup the k3s cluster
Add these words to the `/boot/firmware/cmdline.txt` file:
```
cgroup_enable=cpuset cgroup_enable=memory cgroup_memory=1 swapaccount=1
```

TODO: Install docker-ce

Then set up the rest:
```shell
# Install k3s
curl -sfL https://get.k3s.io | sh -

# Install ArgoCD
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/v2.4.0-rc1/manifests/install.yaml
```


Update Datadog API Key:
```shell
kubectl create configmap datadog-api-key --from-literal=api-key=NEW_TOKEN
```
