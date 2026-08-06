# Only the docker.io pull secret is still sealed-secrets-managed; the
# decommissioned server/channel-bot pairs live in unused/. New secrets go
# through external-secrets (AWS Secrets Manager), not kubeseal.
seal-secrets:
	cat myownradio-dockerconfig-secret.yaml | kubeseal -o yaml > myownradio-dockerconfig-sealedsecret.yaml

unseal-secrets:
	kubectl --namespace myownradio get secret/dockerconfig -o yaml > myownradio-dockerconfig-secret.yaml
