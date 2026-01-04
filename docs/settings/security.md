# Security Settings

Configure security-related settings for OpenGRC.

## Accessing Security Settings

1. Navigate to **Settings** in the admin navigation
2. Click the **Security** tab

## Settings

### Session Timeout

| Setting | Description |
|---------|-------------|
| **Key** | `security.session_timeout` |
| **Type** | Number (minutes) |
| **Default** | 15 minutes |
| **Minimum** | 1 minute |
| **Maximum** | 1440 minutes (24 hours) |

The session timeout controls how long a user can remain inactive before being automatically logged out.

### How Session Timeout Works

1. User logs in to OpenGRC
2. Timer starts tracking inactivity
3. Each interaction (page load, form submission) resets the timer
4. If no activity occurs within the timeout period, the session expires
5. User must log in again

### Choosing a Timeout Value

| Use Case | Recommended Value |
|----------|-------------------|
| High security environments | 5-15 minutes |
| Standard office use | 15-30 minutes |
| Low security/convenience | 60-120 minutes |

### Security Considerations

**Shorter timeouts:**
- Better security against unattended workstations
- May interrupt users during extended reading/thinking
- Recommended for environments with sensitive data

**Longer timeouts:**
- Better user experience
- Less secure against unauthorized access
- Acceptable for secured/trusted environments

## Permissions

Requires the **Manage Preferences** permission to access and modify security settings.

## Related Settings

- [Authentication Settings](authentication.md) - Configure SSO and login methods
