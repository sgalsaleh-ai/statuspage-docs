# TLS & Networking

## Access Methods

### NodePort (default)
Direct access on port 30880. No additional configuration needed.

```
https://<server-ip>:30880
```

### Ingress
Route traffic through Traefik ingress controller with a hostname. Requires DNS pointing to your server.

Configure in the config screen:
- **Access Type**: Ingress
- **Hostname**: Your domain (e.g. `status.example.com`)

## TLS Options

When using Ingress, three TLS modes are available:

### Self-Signed (default)
Traefik serves a built-in self-signed certificate. Browser will show a security warning. Suitable for internal/dev use.

### Let's Encrypt (automatic)
Traefik automatically provisions a trusted certificate from Let's Encrypt. Requires:
- A publicly resolvable hostname
- Port 443 accessible from the internet
- An email address for certificate registration

### Custom Certificate
Upload your own PEM-encoded certificate and private key via the config screen. Use this when you have certificates from your organization's CA.
