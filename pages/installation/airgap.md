# Air Gap Installation

Install {{ app.name }} in an environment without internet access.

## Prerequisites

- Ubuntu 24.04 VM
- No internet access required after downloading the bundle
- Ports 80, 443, 30080 available

## Steps

### 1. Download the air gap bundle (from a machine with internet)

```bash
curl -f "https://replicated.app/embedded/{{ app.slug }}/{{ channel.slug }}?airgap=true" \
  -H "Authorization: {{ license.licenseId }}" \
  -o {{ app.slug }}.tgz
```

### 2. Transfer to the air-gapped machine

Copy the bundle to the target VM using USB, SCP, or any available transfer method.

### 3. Extract and install

```bash
tar -xzf {{ app.slug }}.tgz
sudo ./{{ app.slug }} install --license license.yaml --airgap --yes
```

### 4. Complete setup

Open the installer UI at `https://<server-ip>:30080` and configure your installation.

All container images are included in the bundle — no internet access is needed during or after installation.
