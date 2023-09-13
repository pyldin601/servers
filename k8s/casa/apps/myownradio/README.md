### Update `GITHUB_TOKEN` used for pushing MySQL database backup:

```shell
kubectl -n myownradio create secret generic github-token --from-literal=token=NEW_TOKEN
```
