# S3 Storage Download Tasks

This repository contains Golden Helix server tasks for automating file downloads from S3-compatible storage services.

## Prerequisites

- Access to an S3-compatible storage service
- Access Key ID and Secret Access Key with appropriate permissions
- S3 bucket name

## Setup Instructions

### 1. Get S3 Credentials

To get the necessary credentials for S3 access, follow these steps:

1. Log in to your S3-compatible storage service provider's console
2. Navigate to the security or IAM settings
3. Create or locate an access key pair with the following permissions:
   - `s3:ListBucket` - to list objects in the bucket
   - `s3:GetObject` - to download objects
4. Save both the Access Key ID and Secret Access Key securely

Note: It's recommended to use IAM roles with minimal required permissions for security best practices. Never share or commit your credentials.

## Tasks

The repository contains the following task, which can be run in the Golden Helix server:

### Download S3 Files (`s3_download.task.yaml`)

Downloads files from S3-compatible storage using rclone.

Parameters:
- `s3_provider`: S3-compatible storage provider (default: "AWS")
- `aws_access_key_id`: Access Key ID for authentication
- `aws_secret_access_key`: Secret Access Key for authentication (secret)
- `bucket`: S3 bucket name
- `base_path`: Base path within the bucket (optional, format: "folder/subfolder/...")
- `output_directory`: Directory where files will be downloaded
- `dry_run`: List files only without downloading (default: false)

## Supported Providers

The task supports multiple S3-compatible storage providers including:
- AWS S3
- Alibaba Cloud OSS
- Cloudflare R2
- DigitalOcean Spaces
- Google Cloud Storage
- IBM COS
- Minio
- Wasabi
- And many others

For a complete list of supported providers, see the `s3_provider` parameter choices in the task configuration.

## Notes

- The task uses rclone for efficient file transfers
- The task requires minimal resources (1 CPU core, 1GB memory)
- Make sure your credentials have appropriate permissions
- The base path parameter is optional - if not specified, files will be downloaded from the root of the bucket
- Use dry run mode to preview which files will be downloaded before actually downloading them
