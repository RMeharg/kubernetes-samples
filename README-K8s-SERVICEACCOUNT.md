# Creating a K8s user (SRE)

- Update cgex-users.yaml
- `kubectl apply -f cgex-users.yaml`
- Update secret-token.json
- `kubectl create -f ./secret-token.json`
- kubectl describe secret younghan-token

# Logging In to PKS (Developers)
- kubectl config set-credentials younghan --token=PASTE
- kubectl config set-context younghan-context --cluster=dev --namespace=cgex --user=younghan
- kubectl config use-context younghan-context

Revoke tokens: `kubectl delete secret younghan-token`
