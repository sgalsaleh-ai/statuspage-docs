# Upgrades

## Helm Upgrades

```bash
helm registry login registry.replicated.com \
  --username {{ customer.email }} \
  --password {{ license.licenseId }}

helm upgrade statuspage \
  oci://registry.replicated.com/{{ app.slug }}/{{ channel.slug }}/statuspage \
  --wait --timeout 180s
```

Your data is preserved across upgrades — PostgreSQL uses persistent volumes.

{{#if entitlements.isEmbeddedClusterDownloadEnabled}}
## Embedded Cluster Upgrades

1. Download the new version
2. Run the upgrade command
3. Complete through the web UI

```bash
curl -f "https://replicated.app/embedded/{{ app.slug }}/{{ channel.slug }}" \
  -H "Authorization: {{ license.licenseId }}" \
  -o {{ app.slug }}.tgz
tar -xzf {{ app.slug }}.tgz
sudo ./{{ app.slug }} upgrade --license license.yaml --yes
```

The web UI at `https://<server-ip>:30080` will show the config screen. Review settings and deploy.
{{/if}}

## Checking for Updates

The admin dashboard shows a banner when a new version is available on your channel.
