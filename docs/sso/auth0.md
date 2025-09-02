# OpenGRC Auth0 Authentication Configuration Guide

This document provides step-by-step instructions for configuring Auth0 Single Sign-On (SSO) with OpenGRC.

---

## 1. Prerequisites

Before you begin, ensure you have:

- An active **Auth0 tenant** with administrator access.
- An **OpenGRC** environment accessible to users.
- The **Redirect URL** displayed on the OpenGRC settings screen.

---

## 2. Create Auth0 Application

1. Sign in to your **Auth0 Dashboard**.
2. Navigate to **Applications** → **Applications** → **Create Application**.
3. Enter the following details:
   - **Name**: `OpenGRC`
   - **Application type**: `Regular Web Application`
4. Click **Create**.
5. In the application settings, configure:
   - **Allowed Callback URLs**:  
     Paste the redirect URL from the OpenGRC settings screen.  
     Example:  
     ```
     https://opengrc.test/auth/auth0/callback
     ```
   - **Allowed Logout URLs** (optional).
   - **Allowed Web Origins**: Add your OpenGRC base URL.

---

## 3. Gather Auth0 Credentials

After the application is created, copy the following values:

- **Client ID** → This will be your **Client ID** in OpenGRC.
- **Client Secret** → This will be your **Client Secret** in OpenGRC.
- **Domain** → This will be your **Auth0 domain**, typically:  your-tenant.auth0.com

---

## 4. OpenGRC Authentication Settings

In your OpenGRC portal, navigate to:  
**Settings → General Settings → Authentication → Auth0 Authentication**

Fill in the fields as follows:

- **Enable Auth0 Authentication**: Toggle **ON**
- **Client ID**: Paste the **Client ID** from Auth0
- **Client Secret**: Paste the **Client Secret** from Auth0
- **Domain**: Enter your Auth0 domain (e.g., `your-tenant.auth0.com`)
- **Redirect URL**: Copy this value directly from the OpenGRC settings screen
- **Auto Provision Users**: Toggle ON if you want users created automatically at first login
- **Role**: Select the default role to assign to newly provisioned users

Click **Save** to apply changes.

---

## 5. User Login Flow

Once configured:

1. Users can click **Sign in with Auth0** on the OpenGRC login page.
2. They will be redirected to Auth0 for authentication.
3. If **Auto Provisioning** is enabled, new users will be automatically created in OpenGRC with the assigned role.

---

## 6. Security Recommendations

- Rotate **Client Secrets** regularly.
- Assign a **least-privilege role** for auto-provisioned users.
- Configure **Auth0 rules and policies** to enforce MFA, anomaly detection, and secure access.

---

## 7. Troubleshooting

### Common Issues and Fixes

**Invalid domain**
- Ensure you enter the full Auth0 domain (e.g., `your-tenant.auth0.com`).
- Do not include protocol (`https://`) or trailing slashes.

**Redirect URI mismatch**
- The redirect URI configured in Auth0 must match exactly the one shown in OpenGRC.
- Example:  
  ```
  https://opengrc.test/auth/auth0/callback
  ```

**Invalid client credentials**
- Verify the **Client ID** and **Client Secret** are correct.
- Regenerate a secret in Auth0 if necessary.

**User not provisioned**
- If **Auto Provision Users** is disabled, accounts must be created manually in OpenGRC.
- If enabled, ensure a default role is selected.

**Expired or rotated secret**
- Generate a new secret in Auth0 and update OpenGRC accordingly.

---

