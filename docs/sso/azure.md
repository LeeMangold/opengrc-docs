# Microsoft Azure 

This document provides step-by-step instructions for configuring Azure Single Sign-On (SSO) with OpenGRC.

---

## 1. Prerequisites

Before you begin, ensure you have:

- An active **Microsoft Azure Active Directory (Azure AD)** tenant.
- Administrator access to Azure AD.
- An **OpenGRC** environment accessible to users.
- The **Redirect URL** from OpenGRC (see below).

---

## 2. Azure App Registration

1. Sign in to the [Azure Portal](https://portal.azure.com).
2. Navigate to **Azure Active Directory** → **App registrations** → **New registration**.
3. Enter the following details:
   - **Name**: `OpenGRC`
   - **Supported account types**: Choose based on your needs (e.g., *Accounts in this organizational directory only*).
   - **Redirect URI**:  
     ```
     https://yoururp/auth/azure/callback
     ```
     Get this value from the settings screen.
4. Click **Register**.

---

## 3. Configure Client Credentials

1. After registration, open the new app.
2. Under **Overview**, copy the following values:
   - **Application (client) ID** → This will be your **Client ID** in OpenGRC.
   - **Directory (tenant) ID** → This will be your **Tenant** in OpenGRC.
3. Go to **Certificates & secrets**.
4. Click **New client secret**.
   - Add a description and select an expiration period.
   - Copy the **Value** immediately (you won’t see it again).  
     This will be your **Client Secret** in OpenGRC.

---

## 4. OpenGRC Authentication Settings

In your OpenGRC portal, navigate to:  
**Settings → General Settings → Authentication → Azure Authentication**

Fill in the fields as follows:

- **Enable Azure Authentication**: Toggle **ON**
- **Client ID**: Paste the **Application (client) ID**
- **Client Secret**: Paste the generated **Client Secret**
- **Tenant**: Enter your **Tenant ID**
- **Auto Provision Users**: Toggle ON if you want users created automatically at first login
- **Role**: Select the default role to assign to newly provisioned users

Click **Save** to apply changes.

---

## 5. User Login Flow

Once configured:

1. Users can click **Sign in with Azure** on the OpenGRC login page.
2. They will be redirected to Microsoft for authentication.
3. If **Auto Provisioning** is enabled, new users will be automatically created in OpenGRC with the assigned role.

---

## 6. Security Recommendations

- Rotate **Client Secrets** regularly.
- Assign a **least-privilege role** for auto-provisioned users.
- If possible, configure **Conditional Access policies** in Azure AD for added security (MFA, device compliance, etc.).

---

## 7. Troubleshooting

### Common Issues and Fixes

**Invalid tenant or authority URL**
- Verify that the **Tenant ID** in OpenGRC matches your Azure AD tenant.
- If using multi-tenant, set the tenant to `common`.

**Redirect URI mismatch**
- Ensure the redirect URI in Azure AD matches exactly what is in OpenGRC, including `https://` and trailing paths.
- Example:  
  ```
  https://opengrc.test/auth/azure/callback
  ```

**Invalid client secret**
- Confirm you copied the **Value** of the client secret, not the ID.
- Check that the secret has not expired.

**User not provisioned**
- If **Auto Provision Users** is disabled, an administrator must manually create accounts in OpenGRC before login.
- If enabled, ensure a default role is selected.

**Expired or revoked secret**
- Generate a new secret in **Certificates & secrets** and update OpenGRC with the new value.