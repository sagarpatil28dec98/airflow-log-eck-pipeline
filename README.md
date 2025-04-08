# airflow-log-eck-pipeline

A demo project that deploys:
- Apache Airflow on Kubernetes
- Filebeat for log forwarding
- Elasticsearch + Kibana via ECK
- Managed with ArgoCD

## Quick Start

1. Install ArgoCD and port-forward:

```bash
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
kubectl port-forward svc/argocd-server -n argocd 8081:443
```

2. Login and create apps:
```bash
argocd login 127.0.0.1:8081
argocd app create eck-stack --file manifests/argo/eck-app.yaml
```

3. Sync app:
```bash
argocd app sync eck-stack
```