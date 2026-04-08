# Support Bundles

Support bundles collect diagnostic data from your installation to help with troubleshooting.

## Generate from the App UI

1. Log in to the admin dashboard
2. Click **Generate Support Bundle** on the dashboard
3. The bundle is automatically uploaded to the vendor portal

## Generate from CLI

```bash
curl https://krew.sh/support-bundle | bash
kubectl support-bundle --load-cluster-specs
```

## What's Collected

- Application logs (app, PostgreSQL, Centrifugo, SDK)
- Health endpoint status
- Deployment and StatefulSet status
- Cluster resources and storage class info
- Node readiness

## Upload to Vendor Portal

After generating via CLI, upload the bundle through this portal's support section for analysis.
