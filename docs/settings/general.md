# General Settings

General settings configure basic application information and update behavior.

## Accessing General Settings

1. Navigate to **Settings** in the admin navigation
2. The General tab displays by default

## Settings

### Application Name

| Setting | Description |
|---------|-------------|
| **Key** | `general.name` |
| **Type** | Text |
| **Default** | "OpenGRC" |
| **Constraints** | 2-16 characters |

The name displayed in the application header and browser title.

### Application URL

| Setting | Description |
|---------|-------------|
| **Key** | `general.url` |
| **Type** | URL |
| **Default** | "http://localhost" |

The base URL of your OpenGRC installation. This is used for generating links in emails and reports.

### Update Repository URL

| Setting | Description |
|---------|-------------|
| **Key** | `general.repo` |
| **Type** | URL |
| **Default** | "https://repo.opengrc.com" |

The repository URL used to check for content updates such as new security frameworks and standards.

## Permissions

Requires the **Manage Preferences** permission to access and modify these settings.
