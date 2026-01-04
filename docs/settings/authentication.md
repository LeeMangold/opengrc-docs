# Authentication Settings

OpenGRC supports Single Sign-On (SSO) via OAuth providers. Configure one or more providers to allow users to authenticate with their existing identity provider.

## Accessing Authentication Settings

1. Navigate to **Settings** in the admin navigation
2. Click the **Authentication** tab

## Supported Providers

OpenGRC supports four OAuth providers:

- Microsoft Azure AD
- Okta
- Google Workspace
- Auth0

Each provider can be enabled independently.

## Azure AD Configuration

### Settings

| Setting | Key | Description |
|---------|-----|-------------|
| **Enable Azure Authentication** | `auth.azure.enabled` | Toggle to enable/disable Azure SSO |
| **Client ID** | `auth.azure.client_id` | Application (client) ID from Azure AD |
| **Client Secret** | `auth.azure.client_secret` | Client secret value (encrypted) |
| **Tenant** | `auth.azure.tenant` | Azure AD tenant ID (default: "common") |
| **Redirect URL** | Auto-generated | `{your-url}/auth/azure/callback` |
| **Auto Provision Users** | `auth.azure.auto_provision` | Create users on first login |
| **Role** | `auth.azure.role` | Role assigned to auto-provisioned users |

### Setup Steps

1. Register an application in Azure AD
2. Configure the redirect URI: `https://your-opengrc-url/auth/azure/callback`
3. Create a client secret
4. Copy the Client ID, Client Secret, and Tenant ID to OpenGRC

See [Azure SSO Setup](../sso/azure.md) for detailed instructions.

## Okta Configuration

### Settings

| Setting | Key | Description |
|---------|-----|-------------|
| **Enable Okta Authentication** | `auth.okta.enabled` | Toggle to enable/disable Okta SSO |
| **Client ID** | `auth.okta.client_id` | Okta application client ID |
| **Client Secret** | `auth.okta.client_secret` | Client secret (encrypted) |
| **Base URL** | `auth.okta.base_url` | Your Okta organization URL |
| **Redirect URL** | Auto-generated | `{your-url}/auth/okta/callback` |
| **Auto Provision Users** | `auth.okta.auto_provision` | Create users on first login |
| **Role** | `auth.okta.role` | Role assigned to auto-provisioned users |

### Setup Steps

1. Create an application in Okta Admin Console
2. Configure the redirect URI: `https://your-opengrc-url/auth/okta/callback`
3. Copy the Client ID, Client Secret, and Base URL to OpenGRC

See [Okta SSO Setup](../sso/okta.md) for detailed instructions.

## Google Workspace Configuration

### Settings

| Setting | Key | Description |
|---------|-----|-------------|
| **Enable Google Authentication** | `auth.google.enabled` | Toggle to enable/disable Google SSO |
| **Client ID** | `auth.google.client_id` | Google OAuth client ID |
| **Client Secret** | `auth.google.client_secret` | Client secret (encrypted) |
| **Redirect URL** | Auto-generated | `{your-url}/auth/google/callback` |
| **Auto Provision Users** | `auth.google.auto_provision` | Create users on first login |
| **Role** | `auth.google.role` | Role assigned to auto-provisioned users |

### Setup Steps

1. Create OAuth credentials in Google Cloud Console
2. Configure the redirect URI: `https://your-opengrc-url/auth/google/callback`
3. Copy the Client ID and Client Secret to OpenGRC

See [Google SSO Setup](../sso/google.md) for detailed instructions.

## Auth0 Configuration

### Settings

| Setting | Key | Description |
|---------|-----|-------------|
| **Enable Auth0 Authentication** | `auth.auth0.enabled` | Toggle to enable/disable Auth0 SSO |
| **Client ID** | `auth.auth0.client_id` | Auth0 application client ID |
| **Client Secret** | `auth.auth0.client_secret` | Client secret (encrypted) |
| **Domain** | `auth.auth0.domain` | Your Auth0 tenant domain |
| **Redirect URL** | Auto-generated | `{your-url}/auth/auth0/callback` |
| **Auto Provision Users** | `auth.auth0.auto_provision` | Create users on first login |
| **Role** | `auth.auth0.role` | Role assigned to auto-provisioned users |

### Setup Steps

1. Create an application in Auth0 Dashboard
2. Configure the callback URL: `https://your-opengrc-url/auth/auth0/callback`
3. Copy the Client ID, Client Secret, and Domain to OpenGRC

See [Auth0 SSO Setup](../sso/auth0.md) for detailed instructions.

## Auto-Provisioning

When enabled, auto-provisioning allows new users to be created automatically when they first log in via SSO.

### How It Works

1. User clicks SSO login button
2. User authenticates with identity provider
3. If user doesn't exist in OpenGRC, a new account is created
4. User is assigned the configured default role
5. User is logged in

### Considerations

- Users created via auto-provisioning cannot log in with username/password
- Assign an appropriate default role (typically a limited-access role)
- Users can be promoted to higher roles after creation

## Secret Management

All client secrets are encrypted using Laravel's encryption and stored securely in the database.

**To update a secret:**
1. Enter the new secret value
2. Save settings

**To keep the existing secret:**
- Leave the field blank when saving

The field displays `••••••••` when a secret is stored.

## Permissions

Requires the **Manage Preferences** permission to access and modify authentication settings.
