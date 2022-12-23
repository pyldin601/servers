sealed-secrets:
	cat myownradio-dockerconfig-secret.yaml | kubeseal -o yaml > myownradio-dockerconfig-sealedsecret.yaml
	cat myownradio-server-secret.yaml | kubeseal -o yaml > myownradio-server-sealedsecret.yaml

unseal-secrets:
	kubectl --namespace myownradio get secret/myownradio-server -o yaml > myownradio-server-secret.yaml
	kubectl --namespace myownradio get secret/dockerconfig -o yaml > myownradio-dockerconfig-secret.yaml
