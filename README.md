cat > README.md << 'EOF'
# Local Kubernetes Observability Stack

- kube-prometheus-stack (Prometheus, Alertmanager, Grafana) installed with Helm
- hello-world Helm chart with a ServiceMonitor and a Grafana dashboard
- Runs on Docker Desktop Kubernetes

## Install
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm install monitoring prometheus-community/kube-prometheus-stack -n monitoring --create-namespace -f monitoring-values.yaml
helm install hello-world ./hello-world-chart -n hello --create-namespace
EOF

printf '.vscode/\n*.tgz\n*.log\n.env\nkubeconfig*\n' > .gitignore