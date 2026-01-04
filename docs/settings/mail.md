# Mail Settings

Configure SMTP settings to enable email notifications from OpenGRC.

## Accessing Mail Settings

1. Navigate to **Settings** in the admin navigation
2. Click the **Mail** tab

## SMTP Configuration

| Setting | Key | Description |
|---------|-----|-------------|
| **Mail Host** | `mail.host` | SMTP server hostname |
| **Mail Port** | `mail.port` | SMTP port number |
| **Encryption** | `mail.encryption` | Encryption type |
| **Username** | `mail.username` | SMTP authentication username |
| **Password** | `mail.password` | SMTP authentication password (encrypted) |
| **From Address** | `mail.from` | Email address to send from |

### Common Port Numbers

| Port | Encryption | Usage |
|------|------------|-------|
| 587 | STARTTLS | Recommended for most providers |
| 465 | TLS/SSL | Alternative secure port |
| 25 | None/STARTTLS | Legacy, often blocked |

### Encryption Options

- **TLS** - Full TLS encryption from start
- **STARTTLS** - Upgrade to TLS after connection
- **None** - No encryption (not recommended)

## Testing Email Configuration

After configuring SMTP settings:

1. Click **Send Test Email**
2. A test email is sent to your logged-in email address
3. Check your inbox to verify delivery

If the test fails, check:
- SMTP credentials are correct
- Port is not blocked by firewall
- Sender address is allowed by your mail provider

## AWS SES Configuration

If using Amazon Simple Email Service (SES):

### SMTP Credentials

Use SMTP credentials from the AWS SES console, **not** your AWS access keys.

1. Go to AWS SES Console
2. Navigate to SMTP Settings
3. Click **Create SMTP Credentials**
4. Copy the username (starts with "AKIA") and password

### Common Settings

| Setting | Value |
|---------|-------|
| Host | `email-smtp.{region}.amazonaws.com` |
| Port | 587 |
| Encryption | STARTTLS |
| Username | Your SMTP username |
| Password | Your SMTP password |

### SES Sandbox Mode

New SES accounts start in sandbox mode with restrictions:
- Can only send to verified email addresses
- Limited sending rate

To move out of sandbox:
1. Verify your domain in SES
2. Request production access from AWS

### Troubleshooting SES

- Verify both sender and recipient emails in SES
- Ensure the SMTP hostname region matches your SES region
- Check SES sending quota in the AWS console
- Review SES bounce/complaint metrics

## Email Templates

Email content is configured separately in [Mail Templates](mail-templates.md).

## Permissions

Requires:
- **Manage Preferences** permission
- Storage settings must NOT be locked

## Password Management

The SMTP password is encrypted and stored securely.

**To update the password:**
1. Enter the new password
2. Save settings

**To keep the existing password:**
- Leave the field blank when saving
