# PRO LOGGING

## System Logs
- Setup ELK stack in BOSH
- Update PKS to point to log ingestor IP and port for daemonsets

## Service Mesh / Istio Logs
- Setup fluentd for istio service mesh logging
- Follow https://istio.io/docs/tasks/telemetry/fluentd/ but remove ELK stack, only fluentd configured to BOSH ELK

## Container / App Logs
- Update ELK IP/PORT in `fluentd-daemonset.yaml`
- `kubectl apply -f fluentd-rbac.yaml`
- `kubectl apply -f fluentd-configmap.yaml`
- `kubectl apply -f fluentd-daemonset.yaml`
- Install LogTrail plugin for Kibana - https://github.com/sivasamyk/logtrail/releases
- `kubectl apply -f fluent-bit-rbac.yaml`
- `kubectl apply -f fluent-bit-configmap.yaml`
- `kubectl apply -f fluent-bit-daemonset.yaml`
