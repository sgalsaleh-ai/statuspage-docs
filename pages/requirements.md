# Requirements

## System Requirements

| Resource | Minimum | Recommended |
|----------|---------|-------------|
| CPU | 2 cores | 4 cores |
| Memory | 2 GB | 4 GB |
| Disk | 20 GB | 50 GB |

## Kubernetes Requirements

- Kubernetes **1.26+**
- Default storage class configured
- Outbound internet access (for online installs)

## Supported Distributions

| Distribution | Supported |
|-------------|-----------|
| EKS | Yes |
| GKE | Yes |
| AKS | Yes |
| k3s | Yes |
| kind | Yes (dev/test only) |
| Docker Desktop | No |
| MicroK8s | No |

## Network Requirements

| Endpoint | Port | Purpose |
|----------|------|---------|
| statuspage-proxy.puresoft.app | 443 | Image proxy |
| api.resend.com | 443 | Email notifications |

{{#if entitlements.isEmbeddedClusterDownloadEnabled}}
## Embedded Cluster Requirements

For single-node installs using Embedded Cluster:

- Ubuntu 24.04 (bare metal or VM)
- Ports 80, 443, 30080 available
- Root access
{{/if}}
