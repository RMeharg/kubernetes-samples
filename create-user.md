# Creating a K8s user

- `export K8_USER=ryan`
- `openssl genrsa -out ${K8_USER}.key 4096`
- `openssl req -new -key ${K8_USER}.key -out ${K8_USER}.csr -subj "/CN=${K8_USER}/O=coinone"`
- `openssl x509 -req -in ${K8_USER}.csr -CA PKS_CA.crt -CAkey PKS_CA.key -CAcreateserial -out ${K8_USER}.crt -days 2000`
- `kubectl config set-credentials ${K8_USER} --client-certificate=${K8_USER}.crt --client-key=${K8_USER}.key`
- `kubectl config set-context ${K8_USER} --cluster=dev --namespace=cgex --user=${K8_USER}`
- `kubectl --context=${K8_USER} get pods`
- `vim ${K8_USER}-rb.yaml`

```
kind: RoleBinding
  apiVersion: rbac.authorization.k8s.io/v1beta1
  metadata:
    name: cgex-edit
    namespace: cgex
  subjects:
  - kind: User
    name: K8_USER
    apiGroup: rbac.authorization.k8s.io
  roleRef:
    kind: ClusterRole
    name: edit
    apiGroup: rbac.authorization.k8s.io
```

- `kubectl apply -f ${K8_USER}-rb.yaml`
