# 🚀 Create an S3 Bucket and Upload files using **Terraform**

## 📁 Project Overview
This project demonstrates how to create an Amazon S3 bucket and upload an image using Terraform. It covers setting up Terraform on a Mac, configuring AWS credentials, writing Terraform configuration files, and executing Terraform commands to deploy infrastructure.

---

## 💰 Cost

**FREE** (Eligible under AWS Free Tier)

---

## 🎯 Objectives

To create and manage:

- 🪣 S3 Bucket (with public access blocked)
- 🖼️ Upload an image file to S3 via Terraform
- 🔐 IAM Access via AWS CLI
- 📜 Use of Terraform to provision & destroy infrastructure

---

## ⚠️ Prerequisites

- An AWS account
- A local image (e.g., `image.png`) saved on your machine
- macOS terminal access
- Basic understanding of CLI and cloud infrastructure

---

## 📖 Key Concepts

### 💡 What is Terraform?

Terraform is an **Infrastructure as Code (IaC)** tool that helps you provision cloud resources using code instead of manually configuring them through the console.

### 💡 What is IaC?

**Infrastructure as Code** means writing and managing your cloud infrastructure (like S3, EC2, VPCs) using config files — allowing repeatable, version-controlled infrastructure deployments.

### 💡 What is AWS CLI?

The **AWS Command Line Interface (CLI)** lets you interact with AWS services from your terminal. It's used to configure credentials, run automation scripts, and check service details.

---

## 🛠️ Step-by-Step Guide



### 1. Install Terraform (macOS)
```bash
# Download Terraform binary
cd ~/Downloads
unzip terraform_1.12.0_darwin_arm64.zip
cd terraform_1.12.0_darwin_arm64

# Move Terraform binary to system path (you might need sudo access)
sudo mv terraform /usr/local/bin/

# Check version
terraform -v
```

---

### 2. Create Terraform Project Directory
```bash
mkdir ~/Desktop/XYZ-terraform
cd ~/Desktop/XYZ-terraform
```

---

### 3. Create `main.tf` File
Create and open `main.tf` and paste the following code:

```hcl
provider "aws" {
  region = "us-east-1"
}

resource "aws_s3_bucket" "my_bucket" {
  bucket = "XYZ-unique-bucket-brunda-0211"
  tags = {
    Project = "Create an S3 Bucket with Terraform"
  }
}

resource "aws_s3_bucket_public_access_block" "my_bucket_public_access_block" {
  bucket                  = aws_s3_bucket.my_bucket.id
  block_public_acls       = true
  ignore_public_acls      = true
  block_public_policy     = true
  restrict_public_buckets = true
}
```

---

### 4. Configure AWS CLI
```bash
aws configure
# Provide:
# AWS Access Key ID
# AWS Secret Access Key
# Default region name: us-east-1
# Default output format: json
```

---

### 5. Initialize Terraform
```bash
terraform init
```

---

### 6. Plan the Deployment
```bash
terraform plan
```

---

### 7. Apply the Deployment
```bash
terraform apply
# Type "yes" to confirm
```

---

### 8. Upload an Image to S3 Bucket
Add this to `main.tf` below the previous resources:
```hcl
resource "aws_s3_object" "image" {
  bucket = aws_s3_bucket.my_bucket.id
  key    = "image.png"
  source = "image.png"
}
```

Then run:
```bash
terraform apply
# Type "yes" to confirm
```

Ensure `image.png` is in the same directory as your `main.tf`.

---

### 9. Destroy Resources
```bash
terraform destroy
# Type "yes" to confirm
```

---

### 10. Delete AWS Access Key
1. Go to IAM Console → Users → [Your User] → Security Credentials
2. Scroll to **Access Keys**
3. Click **Delete** on the key you created

---

## ✅ Outcome
- An S3 bucket was successfully created via Terraform
- Public access was restricted
- An image file (`image.png`) was uploaded to the bucket
- Infrastructure was destroyed after testing

---


