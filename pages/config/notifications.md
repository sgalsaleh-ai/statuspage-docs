# Email Notifications

{{#if entitlements.subscriber_notifications}}
Your license includes **Subscriber Notifications**. Users can subscribe to email alerts on your public status page and receive notifications when incidents are created or updated.

Email notifications are powered by the vendor's email infrastructure — no SMTP configuration is required on your end.

## How It Works

1. Visitors to your public status page can enter their email to subscribe
2. When you create or update an incident, subscribers receive an email notification
3. Manage subscribers from the admin dashboard under the **Subscribers** tab

{{/if}}

{{#if entitlements.subscriber_notifications}}
{{else}}
## Not Available

Subscriber notifications are not included in your current license. Contact your vendor to enable this feature.
{{/if}}
