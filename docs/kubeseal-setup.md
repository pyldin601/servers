# How to export and import sealed secrets certificate

## Install kubeseal
```shell
wget https://github.com/bitnami-labs/sealed-secrets/releases/download/v0.17.3/kubeseal-0.17.3-linux-amd64.tar.gz
tar xvf kubeseal-0.17.3-linux-amd64.tar.gz
sudo install -m 755 kubeseal /usr/local/bin/kubeseal && rm kubeseal
```

## Export certificate to STDOUT:
```shell
`kubeseal --fetch-cert`
```

## Import certificate:
```shell
kubeseal --cert cert.pem
```
