# Vendor Portal Settings

Configure the vendor portal, risk scoring, and vendor-related email notifications.

## Accessing Vendor Portal Settings

1. Navigate to **Settings** in the admin navigation
2. Click the **Vendor Portal** tab

## Configuration Tab

### General Settings

#### Enable Vendor Portal

| Setting | Description |
|---------|-------------|
| **Key** | `vendor_portal.enabled` |
| **Type** | Toggle |
| **Default** | Enabled |

Allow vendors to access their portal for document uploads and survey completion.

#### Portal Name

| Setting | Description |
|---------|-------------|
| **Key** | `vendor_portal.name` |
| **Type** | Text |
| **Default** | "Vendor Portal" |

The display name shown to vendors when accessing the portal.

#### Default Survey Template

| Setting | Description |
|---------|-------------|
| **Key** | `vendor_portal.default_survey_template_id` |
| **Type** | Select |

The default survey template used when creating new vendor assessments.

### Magic Link Settings

#### Magic Link Expiry

| Setting | Description |
|---------|-------------|
| **Key** | `vendor_portal.magic_link_expiry_hours` |
| **Type** | Number (hours) |
| **Default** | 24 hours |
| **Minimum** | 1 hour |
| **Maximum** | 168 hours (7 days) |

How long magic links remain valid before expiring.

### Session Settings

#### Session Timeout

| Setting | Description |
|---------|-------------|
| **Key** | `vendor_portal.session_timeout_minutes` |
| **Type** | Number (minutes) |
| **Default** | 120 minutes |
| **Minimum** | 5 minutes |
| **Maximum** | 1440 minutes (24 hours) |

How long a vendor session can remain inactive before requiring re-authentication.

## Risk Scoring Tab

Configure the thresholds for vendor risk ratings based on assessment scores.

### Risk Thresholds

Vendor risk scores range from 0-100, calculated from survey responses. Thresholds determine the risk rating:

| Rating | Key | Default | Score Range |
|--------|-----|---------|-------------|
| **Very Low** | `vendor_portal.risk_threshold_very_low` | 20 | 0-20 |
| **Low** | `vendor_portal.risk_threshold_low` | 40 | 21-40 |
| **Medium** | `vendor_portal.risk_threshold_medium` | 60 | 41-60 |
| **High** | `vendor_portal.risk_threshold_high` | 80 | 61-80 |
| **Critical** | `vendor_portal.risk_threshold_critical` | 100 | 81-100 |

### Adjusting Thresholds

Adjust thresholds based on your organization's risk tolerance:

**More Conservative (lower thresholds):**
- Flags vendors as higher risk sooner
- More vendors require scrutiny
- Suitable for high-security environments

**More Lenient (higher thresholds):**
- Fewer vendors flagged as high risk
- Less administrative overhead
- Suitable for lower-risk vendor relationships

## Email Templates Tab

### Vendor Invitation Email

Sent when inviting a new vendor contact to the portal.

| Setting | Key |
|---------|-----|
| Subject | `mail.templates.vendor_invitation_subject` |
| Body | `mail.templates.vendor_invitation_body` |

**Available Variables:**

| Variable | Description |
|----------|-------------|
| `{{ $vendorName }}` | Vendor organization name |
| `{{ $name }}` | Contact person's name |
| `{{ $email }}` | Contact's email address |
| `{{ $magicLinkUrl }}` | Portal access link |

### Vendor Magic Link Email

Sent when a vendor requests a login link.

| Setting | Key |
|---------|-----|
| Subject | `mail.templates.vendor_magic_link_subject` |
| Body | `mail.templates.vendor_magic_link_body` |

**Available Variables:**

| Variable | Description |
|----------|-------------|
| `{{ $vendorName }}` | Vendor organization name |
| `{{ $name }}` | Contact person's name |
| `{{ $magicLinkUrl }}` | Portal access link |
| `{{ $expiresAt }}` | Link expiration time |

### Vendor Document Expiring Email

Sent when a vendor's document is approaching expiration.

| Setting | Key |
|---------|-----|
| Subject | `mail.templates.vendor_document_expiring_subject` |
| Body | `mail.templates.vendor_document_expiring_body` |

**Available Variables:**

| Variable | Description |
|----------|-------------|
| `{{ $documentTitle }}` | Name of the expiring document |
| `{{ $name }}` | Contact person's name |
| `{{ $expirationDate }}` | Document expiration date |
| `{{ $daysRemaining }}` | Days until expiration |

## Surveys Tab

### Survey Invitation Email

Sent when assigning a survey to an internal user or external respondent.

| Setting | Key |
|---------|-----|
| Subject | `mail.templates.survey_invitation_subject` |
| Body | `mail.templates.survey_invitation_body` |

**Available Variables:**

| Variable | Description |
|----------|-------------|
| `{{ $surveyTitle }}` | Survey name |
| `{{ $name }}` | Recipient's name |
| `{{ $email }}` | Recipient's email |
| `{{ $surveyUrl }}` | Link to complete survey |
| `{{ $dueDate }}` | Survey due date |
| `{{ $description }}` | Survey description |

### Vendor Survey Assigned Email

Sent when a survey is assigned to a vendor contact.

| Setting | Key |
|---------|-----|
| Subject | `mail.templates.vendor_survey_assigned_subject` |
| Body | `mail.templates.vendor_survey_assigned_body` |

**Available Variables:**

| Variable | Description |
|----------|-------------|
| `{{ $surveyTitle }}` | Survey name |
| `{{ $name }}` | Contact's name |
| `{{ $vendorName }}` | Vendor organization name |
| `{{ $dueDate }}` | Survey due date |
| `{{ $portalUrl }}` | Link to vendor portal |

### Survey Reminder Email

Sent to remind vendors of pending surveys.

| Setting | Key |
|---------|-----|
| Subject | `mail.templates.vendor_survey_reminder_subject` |
| Body | `mail.templates.vendor_survey_reminder_body` |

**Available Variables:**

| Variable | Description |
|----------|-------------|
| `{{ $surveyTitle }}` | Survey name |
| `{{ $daysRemaining }}` | Days until due date |
| `{{ $name }}` | Contact's name |
| `{{ $dueDate }}` | Survey due date |
| `{{ $portalUrl }}` | Link to vendor portal |

## Permissions

Requires the **Manage Preferences** permission to access and modify vendor portal settings.

## Related Documentation

- [Vendor Risk Management](../features/vendor-management.md) - Managing vendors and assessments
