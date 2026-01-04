# Report Settings

Configure branding and appearance for generated reports.

## Accessing Report Settings

1. Navigate to **Settings** in the admin navigation
2. Click the **Reports** tab

## Settings

### Custom Report Logo

| Setting | Description |
|---------|-------------|
| **Key** | `report.logo` |
| **Type** | Image upload |
| **Constraints** | Minimum 512px wide |

Upload a custom logo to display on generated PDF reports.

### Supported Formats

- PNG
- JPEG
- GIF
- SVG

### Recommended Specifications

- **Width:** At least 512 pixels
- **Aspect ratio:** Horizontal/landscape orientation works best
- **Background:** Transparent PNG recommended for flexibility

### Uploading a Logo

1. Click the upload area or drag and drop an image
2. Preview the logo in the display area
3. Click **Save** to apply

### Removing the Logo

1. Click the delete/remove button on the current logo
2. Click **Save** to apply

When no custom logo is uploaded, reports use the default OpenGRC branding.

## Where Logos Appear

The custom logo is displayed on:
- Audit reports
- Risk reports
- Compliance reports
- Other generated PDF documents

## File Storage

Uploaded logos are stored in the `report-assets` directory using your configured storage driver (local or cloud storage).

## Permissions

Requires the **Manage Preferences** permission to access and modify report settings.
