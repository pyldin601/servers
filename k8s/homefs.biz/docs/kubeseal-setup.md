# How to export and import sealed secrets certificate

## Install kubeseal
```shell
wget https://github.com/bitnami-labs/sealed-secrets/releases/download/v0.17.5/kubeseal-0.17.5-linux-amd64.tar.gz
tar xvf kubeseal-0.17.5-linux-amd64.tar.gz
sudo install -m 755 kubeseal /usr/local/bin/kubeseal && rm kubeseal
```

## Export certificate to STDOUT:
```shell
`kubeseal --fetch-cert`
```

## Use certificate locally:
```shell
kubeseal --cert cert.pem
```

## Certificate used for encryption/decryption:
```shell
kubectl get secret sealed-secrets-key46mgb -o yaml > sealed-secret.yaml
```
