# Embedded Cluster Installation

Embedded Cluster installs {{ app.name }} on a single bare VM with Kubernetes included — no existing cluster needed.

## Prerequisites

- Ubuntu 24.04 (bare metal or VM)
- Root access
- Ports 80, 443, 30080 available
- Internet access (for online installs)

## Install

### 1. Download the installer

```bash
curl -f "https://replicated.app/embedded/{{ app.slug }}/{{ channel.slug }}" \
  -H "Authorization: {{ license.id }}" \
  -o {{ app.slug }}.tgz
```

### 2. Extract

```bash
tar -xzf {{ app.slug }}.tgz
```

### 3. Run the installer

```bash
sudo ./{{ app.slug }} install --license license.yaml --yes
```

### 4. Complete setup

Open the installer UI at `https://<server-ip>:30080` and walk through the config screen:

- **Database**: Choose embedded (built-in) or external PostgreSQL
- **Networking**: Choose NodePort or Ingress with TLS
- **Application**: Set admin password

### 5. Access the application

After deployment completes, access the app via the NodePort or ingress hostname you configured.

## Upgrades

1. Download the new version:

```bash
curl -f "https://replicated.app/embedded/{{ app.slug }}/{{ channel.slug }}" \
  -H "Authorization: {{ license.id }}" \
  -o {{ app.slug }}.tgz
tar -xzf {{ app.slug }}.tgz
```

2. Run the upgrade:

```bash
sudo ./{{ app.slug }} upgrade --license license.yaml --yes
```

3. Complete through the web UI at `https://<server-ip>:30080`. Review settings and deploy.

Your data is preserved across upgrades.
