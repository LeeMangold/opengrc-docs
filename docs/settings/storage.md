# Storage Settings

Configure where OpenGRC stores uploaded files such as documents, evidence, and reports.

## Accessing Storage Settings

1. Navigate to **Settings** in the admin navigation
2. Click the **Storage** tab

## Storage Options

OpenGRC supports three storage backends:

| Option | Description |
|--------|-------------|
| **Local Private Storage** | Files stored on the server filesystem |
| **Amazon S3** | Files stored in AWS S3 bucket |
| **DigitalOcean Spaces** | Files stored in DigitalOcean Spaces |

## Local Private Storage

The simplest option for single-server deployments.

### Configuration

Select "Local Private Storage" as the storage driver. No additional configuration required.

### Considerations

- Files stored in the `storage/app/private` directory
- Suitable for single-server deployments
- Backup the storage directory regularly
- Not recommended for multi-server or container deployments

## Amazon S3

Store files in AWS S3 for scalability and durability.

### Settings

| Setting | Key | Description |
|---------|-----|-------------|
| **Storage Driver** | `storage.driver` | Select "Amazon S3" |
| **AWS Access Key ID** | `storage.s3.key` | IAM access key (starts with "AKIA") |
| **AWS Secret Access Key** | `storage.s3.secret` | IAM secret key (encrypted) |
| **AWS Region** | `storage.s3.region` | AWS region (e.g., us-east-1) |
| **S3 Bucket Name** | `storage.s3.bucket` | Name of your S3 bucket |

### Setup Steps

1. Create an S3 bucket in AWS Console
2. Create an IAM user with S3 access
3. Generate access keys for the IAM user
4. Configure CORS on the bucket
5. Enter credentials in OpenGRC
6. Test the connection

See [AWS Storage Configuration](aws-storage.md) for detailed setup instructions.

### Testing Connection

Click **Test S3 Connection** to verify your configuration. The test:
1. Writes a test file to the bucket
2. Reads the file back
3. Deletes the test file

If the test fails, check:
- Access key and secret are correct
- IAM user has required permissions
- Bucket exists in the specified region
- CORS is configured on the bucket

## DigitalOcean Spaces

Store files in DigitalOcean Spaces, an S3-compatible object storage service.

### Settings

| Setting | Key | Description |
|---------|-----|-------------|
| **Storage Driver** | `storage.driver` | Select "DigitalOcean Spaces" |
| **Access Key ID** | `storage.digitalocean.key` | Spaces access key |
| **Secret Access Key** | `storage.digitalocean.secret` | Spaces secret key (encrypted) |
| **Region** | `storage.digitalocean.region` | Region code (e.g., nyc3, sfo3, fra1) |
| **Space Name** | `storage.digitalocean.bucket` | Name of your Space |

### Setup Steps

1. Create a Space in DigitalOcean Console
2. Generate Spaces access keys
3. Configure CORS on the Space
4. Enter credentials in OpenGRC
5. Test the connection

### Testing Connection

Click **Test DigitalOcean Connection** to verify your configuration.

## Credential Security

All access keys and secrets are encrypted using Laravel's encryption before storage.

**To update credentials:**
1. Enter the new key/secret
2. Save settings

**To keep existing credentials:**
- Leave the field blank when saving

Fields display `••••••••` when a value is stored.

## Storage Lock

Administrators can lock storage settings to prevent changes. When locked:

- All storage settings are read-only
- A warning message displays: "Storage settings are locked and read-only"
- Contact your administrator to modify settings

## Environment Variables

When storage settings are saved, the following environment variables are updated:

### Amazon S3

```
AWS_ACCESS_KEY_ID=your-key
AWS_SECRET_ACCESS_KEY=your-secret
AWS_DEFAULT_REGION=us-east-1
AWS_BUCKET=your-bucket
FILESYSTEM_DISK=s3
```

### DigitalOcean Spaces

```
DO_SPACES_KEY=your-key
DO_SPACES_SECRET=your-secret
DO_SPACES_REGION=nyc3
DO_SPACES_BUCKET=your-space
DO_SPACES_ENDPOINT=https://nyc3.digitaloceanspaces.com
DO_SPACES_USE_PATH_STYLE=false
FILESYSTEM_DISK=do
```

## Permissions

Requires:
- **Manage Preferences** permission
- Storage settings must NOT be locked

## Related Documentation

- [AWS Storage Configuration](aws-storage.md) - Detailed AWS S3 setup
