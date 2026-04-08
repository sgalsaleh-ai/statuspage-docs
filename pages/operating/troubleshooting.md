# Troubleshooting

## App Not Starting

**Symptoms**: Pod in CrashLoopBackOff or Init state

1. Check if PostgreSQL is ready:
   ```bash
   kubectl get pods -l app.kubernetes.io/name=postgresql
   ```
2. Check app logs:
   ```bash
   kubectl logs deployment/statuspage -c statuspage
   ```
3. The init container waits for the database — if PostgreSQL is slow to start, the app will wait.

## Database Connection Errors

**Symptoms**: "failed to connect to database" in logs

- Verify PostgreSQL is running
- If using external DB, check host, port, credentials, and SSL mode
- Ensure the database exists and the user has permissions

## Real-time Updates Not Working

**Symptoms**: Public status page doesn't update live when you change component status

- Verify Centrifugo is running: `kubectl get pods -l app.kubernetes.io/name=centrifugo`
- Check Centrifugo logs: `kubectl logs deployment/statuspage-centrifugo`
- If using ingress, WebSocket connections may not pass through all proxy configurations

## Health Endpoint

Check the app health at any time:
```bash
kubectl exec deployment/statuspage -c statuspage -- wget -qO- http://localhost:8080/healthz
```

Expected response:
```json
{"status":"ok","checks":{"centrifugo":"ok","database":"ok"}}
```

## Generate a Support Bundle

If you can't resolve the issue, generate a support bundle from the admin dashboard or via CLI and upload it for vendor analysis.
