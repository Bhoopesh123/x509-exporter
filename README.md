# x509-exporter for monitoring expired x509 certificates  

A Prometheus exporter for certificates focusing on expiration monitoring, written in Go. Designed to monitor Kubernetes clusters from inside, it can also be used as a standalone exporter.

Get notified before they expire:

    PEM encoded files, by path or scanning directories
    Kubeconfigs with embedded certificates or file references
    TLS Secrets from a Kubernetes cluster

# 1. Install Grafana  

    helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
    helm repo update
    helm upgrade --install grafana prometheus-community/kube-prometheus-stack

To Search all of the time series data points grouping by job  

    count({__name__=~".+"}) by (job)

# 2. Install X509 Exporter  

    helm upgrade --install x509-certificate-exporter enix/x509-certificate-exporter --values x509-certificate-exporter.values.yaml

# 3. Import the x509 Dashboard  

Import the dashboard by following below reference documentation
    https://grafana.com/grafana/dashboards/13922-certificates-expiration-x509-certificate-exporter/

    Dashboard id: 13922