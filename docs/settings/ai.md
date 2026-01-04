# AI Settings

OpenGRC includes optional AI-powered features that can assist with compliance tasks. These features require an OpenAI API key.

## Accessing AI Settings

1. Navigate to **Settings** in the admin navigation
2. Click the **AI** tab

## Configuration Tab

### Enable AI Suggestions

| Setting | Description |
|---------|-------------|
| **Key** | `ai.enabled` |
| **Type** | Toggle |
| **Default** | Disabled |

Enables or disables AI-powered features throughout the application.

### OpenAI API Key

| Setting | Description |
|---------|-------------|
| **Key** | `ai.openai_key` |
| **Type** | Password (encrypted) |

Your OpenAI API key for accessing AI services. The key is encrypted and stored securely.

**To update the API key:**
1. Enter the new key in the field
2. Save settings

**To keep the existing key:**
- Leave the field blank when saving

## Quota Usage Tab

The quota usage tab displays current AI usage statistics:

| Metric | Description |
|--------|-------------|
| **Prompt Tokens** | Tokens used for prompts today |
| **Response Tokens** | Tokens received in responses today |
| **Quota Resets At** | Time when daily quota resets (midnight) |
| **AI_PROMPT_QUOTA** | Configured daily prompt token limit |
| **AI_RESPONSE_QUOTA** | Configured daily response token limit |

### Configuring Quotas

AI quotas are configured in the `.env` file:

```
AI_PROMPT_QUOTA=100000
AI_RESPONSE_QUOTA=100000
```

Set a quota to `0` to disable that limit.

Quotas reset automatically at midnight.

## Permissions

Requires the **Manage Preferences** permission to access and modify AI settings.
