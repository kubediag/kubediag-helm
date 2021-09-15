# KubeDiag Helm

This Helm chart installs KubeDiag in a Kubernetes cluster.

## Prerequisites

Please make sure the enviroment for installing KubeDiag fulfills the following requirements:

* [Kubernetes](https://github.com/kubernetes/kubernetes) 1.16+
* [Helm](https://github.com/helm/helm) 3.0+
* [Cert Manager](https://github.com/jetstack/cert-manager) 1.0+

## Installation

Run the following command to install KubeDiag via Helm:

```bash
helm repo add kubediag https://kubediag.github.io/kubediag-helm
helm repo update
helm install kubediag kubediag/kubediag-helm --create-namespace --namespace kubediag
```

Prometheus operator related resources are disabled by default. To enable related monitors, specify the '--set' flag when install kubediag (Before this step, make sure you have deployed prometheus operator):

```bash
helm install kubediag kubediag/kubediag-helm --create-namespace --namespace kubediag --set prometheus.serviceMonitor.selfMonitor=true
```

Check the status of KubeDiag by running the command:

```bash
kubectl get all --namespace kubediag
```

## Uninstallation

Run the following command to uninstall KubeDiag via Helm:

```bash
helm uninstall --namespace kubediag kubediag
```
