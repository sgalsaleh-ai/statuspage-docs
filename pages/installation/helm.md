# Helm Installation

## Prerequisites

- Kubernetes cluster meeting the [Requirements](/pages/requirements.md)
- Helm 3.x installed
- `kubectl` configured to access your cluster

## Install

### 1. Log in to the registry

```bash
helm registry login registry.replicated.com \
  --username {{ customer.email }} \
  --password {{ license.licenseId }}
```

### 2. Install preflight checks (optional)

```bash
curl https://krew.sh/preflight | bash
helm template statuspage oci://registry.replicated.com/{{ app.slug }}/{{ channel.slug }}/statuspage | kubectl preflight -
```

### 3. Install the chart

```bash
helm install statuspage \
  oci://registry.replicated.com/{{ app.slug }}/{{ channel.slug }}/statuspage \
  --set image.tag=latest \
  --wait --timeout 180s
```

### 4. Access the application

```bash
kubectl port-forward svc/statuspage 9090:8080
```

Open http://localhost:9090 in your browser.

## Upgrade

```bash
helm upgrade statuspage \
  oci://registry.replicated.com/{{ app.slug }}/{{ channel.slug }}/statuspage \
  --wait --timeout 180s
```

Your data is preserved across upgrades — PostgreSQL uses persistent volumes.

The admin dashboard shows a banner when a new version is available.

## Uninstall

```bash
helm uninstall statuspage
```
