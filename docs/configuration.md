# Configuring AWS for OpenGRC

This guide will walk you through the steps required to configure AWS S3 buckets and IAM policies for use with OpenGRC.

---

## 1. Create S3 Buckets

You will need an S3 bucket for OpenGRC, for example:

- `opengrc`

You can create these buckets via the AWS Console or AWS CLI:

```bash
aws s3 mb s3://opengrc
```

---

## 2. Configure CORS for Each Bucket

CORS (Cross-Origin Resource Sharing) is a security feature implemented by web browsers to control how web applications running at one origin (domain) can interact with resources from a different origin. By default, web browsers block requests for resources (such as files in an S3 bucket) that come from a different domain than the one serving the web application.

When OpenGRC is running in your browser or on a different server, it may need to access files stored in your AWS S3 bucket. Without a proper CORS configuration, these requests would be blocked by the browser, and OpenGRC would not be able to upload, download, or manage files in your S3 bucket.

By setting a CORS policy on your S3 bucket, you explicitly allow OpenGRC (and other approved origins) to interact with your bucket’s contents. The CORS configuration specifies which HTTP methods (GET, PUT, POST, etc.), headers, and origins are permitted, as well as which response headers should be exposed to the client.

To allow OpenGRC to interact with your S3 buckets from your application, you must set a CORS (Cross-Origin Resource Sharing) policy.

1. Go to the AWS S3 Console.
2. Select your bucket (e.g., `opengrc`).
3. Go to the **Permissions** tab.
4. Click on **CORS configuration**.
5. Paste the following configuration and save:

```json
[
    {
        "AllowedHeaders": ["*"],
        "AllowedMethods": ["GET", "PUT", "POST", "DELETE", "HEAD"],
        "AllowedOrigins": ["*"],
        "ExposeHeaders": ["ETag", "x-amz-request-id"],
        "MaxAgeSeconds": 3600
    }
]
```

**Note: You must run OpenGRC using HTTPS or you will get CORS errors regardless of the above settings.**


---

## 3. Create an IAM Policy for OpenGRC

You need an IAM policy that allows OpenGRC to list, get, put, and delete objects in your S3 buckets.

1. Go to the AWS IAM Console.
2. Click **Policies** > **Create policy**.
3. Select the **JSON** tab and paste the following policy, replacing the bucket names if needed:

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "AllowListingOfTestBucket",
            "Effect": "Allow",
            "Action": "s3:ListBucket",
            "Resource": "arn:aws:s3:::opengrc"
        },
        {
            "Sid": "AllowObjectActionsOnTestBucket",
            "Effect": "Allow",
            "Action": [
                "s3:GetObject",
                "s3:PutObject",
                "s3:DeleteObject"
            ],
            "Resource": "arn:aws:s3:::opengrc/*"
        }
    ]
}
```

4. Click **Next**, give your policy a name (e.g., `OpenGRC-S3-Access`), and create the policy.

---

## 4. Attach the Policy to a User or Role

1. Go to **Users** or **Roles** in the IAM Console.
2. Select the user or role that OpenGRC will use.
3. Click **Add permissions** > **Attach policies**.
4. Search for the policy you just created (e.g., `OpenGRC-S3-Access`) and attach it.

---

## 5. Use the IAM Credentials in OpenGRC

- Obtain the Access Key ID and Secret Access Key for the IAM user or role.
- Configure these credentials in your OpenGRC application as required (see OpenGRC’s application configuration documentation for details).

---

**Your AWS environment is now configured for use with OpenGRC!**

If you need to restrict access further, adjust the bucket names, allowed origins, or actions in the above policies as appropriate for your environment.