# Mail Templates

Customize the content of system-generated emails sent by OpenGRC.

## Accessing Mail Templates

1. Navigate to **Settings** in the admin navigation
2. Click the **Mail Templates** tab

## Available Templates

### Password Reset Email

Sent when a user requests a password reset.

| Setting | Key |
|---------|-----|
| Subject | `mail.templates.password_reset_subject` |
| Body | `mail.templates.password_reset_body` |

### New Account Email

Sent when an administrator creates a new user account.

| Setting | Key |
|---------|-----|
| Subject | `mail.templates.new_account_subject` |
| Body | `mail.templates.new_account_body` |

### Evidence Request Email

Sent when a data request is assigned to a user for evidence collection.

| Setting | Key |
|---------|-----|
| Subject | `mail.templates.evidence_request_subject` |
| Body | `mail.templates.evidence_request_body` |

## Editing Templates

Each template has two fields:

1. **Subject** - The email subject line (plain text)
2. **Body** - The email body content (rich HTML editor)

### Rich Editor Features

The body editor supports:
- Text formatting (bold, italic, underline)
- Headings and paragraphs
- Lists (bulleted and numbered)
- Links

**Note:** Image and file attachments are disabled for security.

## Template Variables

Templates support variable substitution using the `{{ $variableName }}` syntax.

Available variables depend on the email type. Common variables include:
- User name
- Email address
- Reset links
- Request details

Variables are automatically replaced with actual values when emails are sent.

## Best Practices

- **Keep subjects concise** - Clear, descriptive subject lines improve open rates
- **Include essential information** - Users should understand the action needed
- **Test after changes** - Send test emails to verify formatting
- **Use professional tone** - Emails represent your organization

## Permissions

Requires:
- **Manage Preferences** permission
- Storage settings must NOT be locked

## Related Settings

- [Mail Settings](mail.md) - Configure SMTP server
- [Trust Center Settings](trust-center.md) - Trust Center email templates
- [Vendor Portal Settings](vendor-portal.md) - Vendor portal email templates
