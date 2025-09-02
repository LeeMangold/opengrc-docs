# OpenGRC Google Authentication Configuration Guide

This document provides step-by-step instructions for configuring Google Single Sign-On (SSO) with OpenGRC.

---

## 1. Prerequisites

Before you begin, ensure you have:

- A **Google Cloud Platform (GCP)** project with administrator access.
- An **OpenGRC** environment accessible to users.
- The **Redirect URL** displayed on the OpenGRC settings screen.

---

## 2. Create Google OAuth Credentials

1. Go to the [Google Cloud Console](https://console.cloud.google.com/).
2. Select your project or create a new one.
3. Navigate to **APIs & Services** → **OAuth consent screen**.
   - Configure the app name, support email, and authorized domains.
   - Save your changes.
4. Navigate to **APIs & Services** → **Credentials**.
5. Click **Create Credentials** → **OAuth client ID**.
6. Choose:
   - **Application type**: `Web application`
   - **Name**: `OpenGRC`
7. Under **Authorized redirect URIs**, paste the redirect URL from the OpenGRC settings screen.  
*(Always use the exact value shown in your OpenGRC settings.)*
8. Click **Create**.

---

## 3. Gather Google Credentials

After creating the OAuth client, copy the following values:

- **Client ID** → This will be your **Client ID** in OpenGRC.
- **Client Secret** → This will be your **Client Secret** in OpenGRC.

---

## 4. OpenGRC Authentication Settings

In your OpenGRC portal, navigate to:  
**Settings → General Settings → Authentication → Google Authentication**

Fill in the fields as follows:

- **Enable Google Authentication**: Toggle **ON**
- **Client ID**: Paste the **Client ID** from Google
- **Client Secret**: Paste the **Client Secret** from Google
- **Redirect URL**: Copy this value directly from the OpenGRC settings screen
- **Auto Provision Users**: Toggle ON if you want users created automatically at first login
- **Role**: Select the default role to assign to newly provisioned users

Click **Save** to apply changes.

---

## 5. User Login Flow

Once configured:

1. Users can click **Sign in with Google** on the OpenGRC login page.
2. They will be redirected to Google for authentication.
3. If **Auto Provisioning** is enabled, new users will be automatically created in OpenGRC with the assigned role.

---

## 6. Security Recommendations

- Rotate **Client Secrets** periodically.
- Assign a **least-privilege role** for auto-provisioned users.
- Enforce **Google Workspace security settings** such as MFA, context-aware access, and session controls.

---

## 7. Troubleshooting

### Common Issues and Fixes

**Redirect URI mismatch**
- Ensure the redirect URI configured in Google Cloud matches exactly the one shown in OpenGRC.
- Example:
 ```
 https://opengrc.test/auth/google/callback
 ```

**Invalid client credentials**
- Verify the **Client ID** and **Client Secret** values are correct.
- Regenerate a secret in Google Cloud if necessary.

**User not provisioned**
- If **Auto Provision Users** is disabled, accounts must be manually created in OpenGRC.
- If enabled, ensure a default role is selected.

**Access blocked by Google**
- Ensure you configured the **OAuth consent screen** properly and included your OpenGRC domain in authorized domains.

---

