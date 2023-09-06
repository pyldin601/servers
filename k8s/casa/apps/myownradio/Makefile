seal-secrets:
	cat myownradio-dockerconfig-secret.yaml | kubeseal -o yaml > myownradio-dockerconfig-sealedsecret.yaml
	cat myownradio-server-secret.yaml | kubeseal -o yaml > myownradio-server-sealedsecret.yaml
	cat myownradio-channel-bot-secret.yaml | kubeseal -o yaml > myownradio-channel-bot-sealedsecret.yaml

unseal-secrets:
	kubectl --namespace myownradio get secret/myownradio-server -o yaml > myownradio-server-secret.yaml
	kubectl --namespace myownradio get secret/dockerconfig -o yaml > myownradio-dockerconfig-secret.yaml
	kubectl --namespace myownradio get secret/channel-bot-secret -o yaml > myownradio-channel-bot-secret.yaml
