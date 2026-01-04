# Trust Center Settings

Configure the Trust Center's NDA requirements and email notifications.

## Accessing Trust Center Settings

1. Navigate to **Settings** in the admin navigation
2. Click the **Trust Center** tab

## NDA Tab

### Require NDA Agreement

| Setting | Description |
|---------|-------------|
| **Key** | `trust_center.nda_required` |
| **Type** | Toggle |
| **Default** | Enabled |

When enabled, users requesting access to protected documents must agree to the NDA before their request is submitted.

### NDA Text

| Setting | Description |
|---------|-------------|
| **Key** | `trust_center.nda_text` |
| **Type** | Rich HTML editor |

The NDA content displayed to users when requesting access to protected documents.

**Editor Features:**
- Text formatting (bold, italic, underline)
- Headings and paragraphs
- Lists (bulleted and numbered)
- Links

**Note:** Image and file attachments are disabled for security.

## Email Templates Tab

### Access Request Notification

Sent to administrators when a new access request is submitted.

| Setting | Key |
|---------|-----|
| Subject | `mail.templates.trust_center_access_request_subject` |
| Body | `mail.templates.trust_center_access_request_body` |

**Available Variables:**

| Variable | Description |
|----------|-------------|
| `{{ $requesterName }}` | Name of the person requesting access |
| `{{ $requesterEmail }}` | Email of the requester |
| `{{ $requesterCompany }}` | Company of the requester |
| `{{ $reason }}` | Reason provided for the request |
| `{{ $ndaAgreed }}` | Whether NDA was agreed to |
| `{{ $approvalUrl }}` | Link to approve/reject the request |
| `{{ $documentCount }}` | Number of documents requested |

### Access Approved Email

Sent to the requester when their access request is approved.

| Setting | Key |
|---------|-----|
| Subject | `mail.templates.trust_center_access_approved_subject` |
| Body | `mail.templates.trust_center_access_approved_body` |

**Available Variables:**

| Variable | Description |
|----------|-------------|
| `{{ $requesterName }}` | Name of the approved requester |
| `{{ $requesterEmail }}` | Email of the requester |
| `{{ $accessUrl }}` | Magic link to access documents |
| `{{ $expiryHours }}` | Hours until link expires |
| `{{ $expiresAt }}` | Expiration date/time |
| `{{ $documentCount }}` | Number of documents accessible |

### Access Rejected Email

Sent to the requester when their access request is rejected.

| Setting | Key |
|---------|-----|
| Subject | `mail.templates.trust_center_access_rejected_subject` |
| Body | `mail.templates.trust_center_access_rejected_body` |

**Available Variables:**

| Variable | Description |
|----------|-------------|
| `{{ $requesterName }}` | Name of the rejected requester |
| `{{ $requesterEmail }}` | Email of the requester |
| `{{ $reviewNotes }}` | Notes/reason provided by reviewer |

## Permissions

Requires the **Manage Preferences** permission to access and modify Trust Center settings.

## Related Documentation

- [Trust Center Feature](../features/trustcenter.md) - Using the Trust Center
