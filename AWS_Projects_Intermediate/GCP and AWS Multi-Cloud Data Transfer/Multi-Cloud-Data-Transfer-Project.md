# Multi-Cloud Data Transfer with AWS and GCP

## 🚀 Project Summary
**Level**: Intermediate  
**Duration**: 60 minutes  
**Cost**: $0 (covered by AWS Free Tier and GCP Free Trial)

This hands-on project walks you through securely transferring data from AWS S3 to Google Cloud Storage using GCP’s Storage Transfer Service. You'll build a cross-cloud integration with identity federation and role-based access.

---


## 🧰 Tools & Services Used
- AWS S3
- AWS IAM
- GCP Cloud Storage
- GCP Storage Transfer Service 
- (Optional) Amazon SQS for real-time use cases

---

## 📌 Key Concepts
- Multi-cloud data architecture
- Identity Federation
- IAM Role trust relationships
- Batch and event-driven transfers
- Manifest-based selective file transfers

---

## 📝 What You'll Do
- 🪣 Create buckets in AWS and GCP
- 🔐 Set up IAM roles for secure cross-cloud access
- ⚙️ Configure and run a batch transfer job
- 💎 (Optional) Set up selective transfer with a manifest

---

## 🔄 Step-by-Step Instructions

### Step 1: Create an S3 Bucket in AWS
1. Log in to the AWS Management Console as your IAM Admin  user.
2.  Open AWS Console → Search for **S3**
3. Click **Create bucket** → Name it: `data-transfer-source-yourname`
4. Leave defaults → Click **Create bucket**
5. Select bucket → Upload 1–3 files → Click **Upload**

### Step 2: Create a Free GCP Account
1. Visit [cloud.google.com](https://cloud.google.com/)
2. Click **Get Started for Free** → Sign in with a Google account
3. Create payments profile (choose **Individual**, enter address)
4. Add a credit card (identity check only)
5. Select **Student** as role → Finish setup

### Step 3: Configure Storage Transfer in GCP
1. Go to **Storage Transfer** in GCP Console
2. Click **Create Transfer Job**
3. Source: **Amazon S3** → Destination: **Google Cloud Storage**
4. Scheduling: **Batch** → Click **Next Step**

### Step 4: Enter Your S3 Bucket Name
- Bucket or folder = `data-transfer-source-yourname`
- Click **Next Step**

### Step 5: Configure GCP Credentials
- Select **AWS IAM Role for Identity Federation**
- Leave this tab open for now

### Step 6: Get GCP Subject ID
1. Go to: [Service Accounts API](https://cloud.google.com/storage-transfer/docs/reference/rest/v1/googleServiceAccounts/get)
### 📌 Retrieve Your GCP Project ID

To use the Google Service Accounts API method, you’ll need your **GCP project ID**.

1. Head back to your **Storage Transfer** tab in the **GCP Console**.
2. In the top bar, locate and **select your project** (e.g., `My First Project`).
3. **Copy** the **Project ID** (not the name).
4. Return to the [Google Service Accounts API page](https://cloud.google.com/storage-transfer/docs/reference/rest/v1/googleServiceAccounts/get).
5. Paste your **Project ID** into the `projectId` field in the **Try this method** panel on the right.
6. Click **Execute**.
7. scroll down to the **Response** section.
2. Locate the value labeled `"subjectId"`.
3. **Copy** the `subjectId` — you’ll need to paste it into your IAM trust policy in AWS.

### Step 7: Create IAM Role in AWS
1. Go to **IAM → Roles → Create Role**
2. Choose **Custom trust policy** and paste:
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": {
        "Federated": "accounts.google.com"
      },
      "Action": "sts:AssumeRoleWithWebIdentity",
      "Condition": {
        "StringEquals": {
          "accounts.google.com:sub": "SUBJECT_ID"
        }
      }
    }
  ]
}
```
3. Replace `SUBJECT_ID` with the copied value
4. Attach policy: **AmazonS3ReadOnlyAccess**
5. Role name: `data-transfer-gcp-role`
6. In the Description, add the following text: Role that grants my GCP project's Storage Transfer Service Read Only access to my S3 buckets. Created this IAM role as a part of NextWork's multi-cloud project.
7. Create the role

### Step 8: Complete GCP Configuration
- Paste your IAM role’s **ARN** into **Role ARN** field in GCP
- Click **Next Step**

### Step 9: Create a GCP Storage Bucket
1. Click **Browse → Create new bucket**
2. Name it: `data-transfer-destination-gcp-yourname`
3. Region: Match AWS bucket location
4. Storage Class: **Standard**
5. Leave access defaults → Disable **Soft delete**
6. Confirm **Public access prevention**
7. Click **Select → Next Step**

### Step 10: Schedule the Transfer Job
1. Choose **Run Once → Starting Now**
2. Description: `Data transfer from S3 to GCP for project`
3. Leave defaults → Click **Create**

### Step 11: Monitor the Job
- Monitor **Operation Status** → Wait for **Success**

### Step 12: Verify Data Transfer
1. In GCP Console → Go to **Storage > Buckets**
2. Open your bucket → Click **Refresh**
3. Confirm your files are present

---

## 🧹 Cleanup Checklist
- [ ] Delete Transfer Jobs in GCP
- [ ] Delete GCP Storage Bucket
- [ ] Delete IAM Role in AWS
- [ ] Delete AWS S3 Bucket
- [ ] Delete local manifest file (if used)

---

## ✅ Outcome
You now know how to:
- Transfer data securely across AWS and GCP
- Use identity federation to connect cloud services
- Build batch and filtered data pipelines

---

## 📘 Q&A Section

### ❓What is multi-cloud?
**Multi-cloud** refers to using more than one cloud provider (e.g., AWS + GCP) for improved flexibility, reliability, and cost savings.

### ❓Why use identity federation instead of access keys?
Identity federation lets GCP assume an AWS IAM role **securely and temporarily** using short-lived credentials—far safer than storing access keys.

### ❓Why do I need a subject ID?
The **subject ID** uniquely identifies your GCP project's service account. It’s used in the trust policy so AWS knows GCP is authorized.

### ❓What does the trust policy do?
It allows GCP’s Storage Transfer Service to assume the AWS IAM role using its subject ID via **Web Identity Federation**.

### ❓Why choose Standard storage class?
It offers high availability and low latency for frequently accessed data—perfect for active backups or application data.

### ❓What happens if you skip cleanup?
Leaving resources (like buckets and roles) running may lead to unnecessary charges or security risks.

---

**🎉 Congrats! You've mastered secure multi-cloud data transfers using IAM roles and federation.**
