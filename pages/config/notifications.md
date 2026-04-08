# Email Notifications

{{#ifEquals entitlements.subscriber_notifications "true"}}

Your license includes **Subscriber Notifications**. This feature is active on your installation.

Email notifications are powered by the vendor's email infrastructure — no SMTP configuration is required on your end.

## How It Works

1. Visitors to your public status page can enter their email to subscribe
2. When you create or update an incident, subscribers receive an email notification
3. Manage subscribers from the admin dashboard under the **Subscribers** tab

{{/ifEquals}}

{{#ifEquals entitlements.subscriber_notifications "false"}}

## Not Available

Subscriber notifications are not included in your current license. Contact your vendor to enable this feature.

{{/ifEquals}}
