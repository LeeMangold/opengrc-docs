# Okta SSO

This document provides step-by-step instructions for configuring Okta Single Sign-On (SSO) with OpenGRC.

---

## 1. Prerequisites

Before you begin, ensure you have:

- An active **Okta tenant** with administrator access.
- An **OpenGRC** environment accessible to users.
- The **Redirect URL** from OpenGRC (see below).

---

## 2. Okta Application Setup

1. Sign in to your **Okta Admin Console**.
2. Navigate to **Applications** → **Applications** → **Create App Integration**.
3. Select:
   - **Sign-in method**: `OIDC - OpenID Connect`
   - **Application type**: `Web Application`
4. Click **Next**.
5. Enter the following details:
   - **App name**: `OpenGRC`
   - **Sign-in redirect URIs**:  
     ```
     https://opengrc.test/auth/okta/callback
     ```
   - **Sign-out redirect URIs** (optional).
6. Under **Assignments**, choose how to assign the app to users/groups.
7. Click **Save**.

---

## 3. Gather Okta Credentials

After the app is created, copy the following values:

- **Client ID** → This will be your **Client ID** in OpenGRC.
- **Client Secret** → This will be your **Client Secret** in OpenGRC.
- **Okta Domain (Base URL)** → Found in the Okta Admin Console, typically looks like:   https://your-org.okta.com

---

## 4. OpenGRC Authentication Settings

In your OpenGRC portal, navigate to:  
**Settings → General Settings → Authentication → Okta Authentication**

Fill in the fields as follows:

- **Enable Okta Authentication**: Toggle **ON**
- **Client ID**: Paste the **Client ID** from Okta
- **Client Secret**: Paste the **Client Secret** from Okta
- **Base URL**: Enter your **Okta domain** (e.g., `https://your-org.okta.com`)
- **Redirect URL**:  (Get this from OpenGRC Settings Screen)
- **Auto Provision Users**: Toggle ON if you want users created automatically at first login
- **Role**: Select the default role to assign to newly provisioned users

Click **Save** to apply changes.

---

## 5. User Login Flow

Once configured:

1. Users can click **Sign in with Okta** on the OpenGRC login page.
2. They will be redirected to Okta for authentication.
3. If **Auto Provisioning** is enabled, new users will be automatically created in OpenGRC with the assigned role.

---

## 6. Security Recommendations

- Rotate **Client Secrets** regularly.
- Assign a **least-privilege role** for auto-provisioned users.
- Use **Okta security policies** (MFA, adaptive access, device trust) to enforce secure access.

---

## 7. Troubleshooting

### Common Issues and Fixes

**Invalid Base URL**
- Ensure you enter the full Okta domain (e.g., `https://your-org.okta.com`).
- Do not include trailing slashes.

**Redirect URI mismatch**
- The redirect URI configured in Okta must match exactly what is in OpenGRC.
- Example:  
  ```
  https://opengrc.test/auth/okta/callback
  ```

**Invalid client credentials**
- Double-check the **Client ID** and **Client Secret** values.
- Regenerate a secret in Okta if necessary.

**User not provisioned**
- If **Auto Provision Users** is disabled, users must be created manually in OpenGRC.
- If enabled, ensure a default role is selected.

**Expired or revoked secret**
- Generate a new client secret in Okta and update OpenGRC accordingly.

---


