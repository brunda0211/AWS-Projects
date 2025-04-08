# 🚀 DevOps Engineer Onboarding: EC2 + IAM Setup

## 🧭 Introduction

We’re onboarding a DevOps Engineer to our dynamic team at **XYZ Company**. This engineer should have access to the **development EC2 instance**, but **not** the production instance. We want to avoid any accidental shutdowns or unintended changes being pushed to the production environment while they're still testing.

To manage access, we’ll use **AWS Identity and Access Management (IAM)**, which controls who is **authenticated** (signed in) and **authorized** (granted permissions) within the AWS console.

In this project, we’ll launch an **EC2 instance**, and then use **IAM policies**, **user groups**, and an **AWS Account Alias** to control access. The policy we create will grant **full access only to EC2 instances tagged with** `ENV: development`.

---

## 💰 Cost

**FREE** (Eligible under AWS Free Tier)

---

## 🎯 Objectives

To create:

- 💻 EC2 instances  
- 📏 IAM Policies  
- 👩‍👩‍👧‍👧 IAM Users and User Groups  
- 🔖 AWS Account Alias  

---

## ⚠️ Heads Up! Before You Begin...

### 🔐 What is AWS IAM?

AWS IAM (Identity and Access Management) enables secure control of access to AWS resources. It allows you to create users, groups, and roles with specific permissions, enhancing security and ensuring proper resource management.

### 💻 What is EC2?

Amazon EC2 (Elastic Compute Cloud) is a cloud service that allows you to rent virtual machines over the internet. Think of them like personal computers you can access online—customizable and scalable to suit your needs. You can use EC2 instances for running applications, hosting websites, processing data, and more.

### 🏷️ Tags

Tags are labels you can attach to AWS resources for organization. Tags in EC2 help you organize, manage, and identify resources efficiently.

### 📦 What is AMI?

AMI (Amazon Machine Image) is a template or blueprint used to create EC2 instances. It contains the operating system and any applications or configurations needed to launch the instance.

### ⚙️ What is Instance Type?

Instance types define the hardware resources for your EC2 instance, including CPU, memory, and storage. AMIs provide the software; instance types provide the horsepower.

### 📜 IAM Policies

IAM policies define permissions for IAM users, groups, or roles — specifying what actions they can or cannot perform on which resources.

### 📄 JSON Policy Structure

When creating a JSON policy, you define:
- `Effect`: Allow or Deny
- `Action`: AWS operations (e.g. `ec2:StartInstances`)
- `Resource`: AWS resources affected by the rule

### 🔖 Account Alias

An Account Alias is a friendly name for your AWS account you can use instead of your 12-digit account ID.

Default sign-in URL:  
`https://Your_Account_ID.signin.aws.amazon.com/console/`

Alias sign-in URL:  
`https://Your_Account_Alias.signin.aws.amazon.com/console/`

---

## 👥 IAM Users and User Groups

### **Users**

IAM users represent individuals or applications. Each user has unique credentials and specific permissions.

### **User Groups**

User groups are collections of IAM users. Assigning a policy to a group makes managing permissions easier for multiple users.

---

## 🔧 Step-by-Step Implementation

### 1. Launch EC2 Instances

1. Log in to your AWS Console.
2. Open the EC2 service.
3. Set your Region.
4. Click **Launch instance**.
5. Set:
   - Name: `XYZ-prod-name`
   - Tags:
     - `Key`: `Env`
     - `Value`: `production`
6. Choose Free Tier AMI and Instance Type.
7. Proceed without a key pair.
8. Launch the instance.

Repeat the same process for development:

- Name: `XYZ-dev-name`
- Tags:  
  - `Env`: `development`

You should now see **two EC2 instances**, one for production and one for development.

---

### 2. Create an IAM Policy

1. Go to the IAM console.
2. Navigate to **Policies > Create Policy**.
3. Switch to **JSON** tab.
4. Paste the following policy:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "ec2:*",
      "Resource": "*",
      "Condition": {
        "StringEquals": {
          "ec2:ResourceTag/Env": "development"
        }
      }
    },
    {
      "Effect": "Allow",
      "Action": "ec2:Describe*",
      "Resource": "*"
    },
    {
      "Effect": "Deny",
      "Action": [
        "ec2:DeleteTags",
        "ec2:CreateTags"
      ],
      "Resource": "*"
    }
  ]
}
```


6. Click **Next**  
7. Fill in the policy details:  
   - **Name**: `XYZDevEnvironmentPolicy`  
   - **Description**: IAM Policy for NextWorks development environment  
8. Click **Create policy**

✅ Awesome, the permission policy is all set up!  
Now that our engineer has access to the development instance, they’re excited and ready to dive in.

---

### 3. Create an AWS Account Alias

1. Head to your **IAM dashboard**  
2. On the right-hand side, choose **Create** under **Account Alias**  
3. In the **Preferred alias** field, enter: `XYZ-alias-name`  
4. Click **Create alias**

---

### 4. Create IAM Users and User Groups

> 📝 **Note:** Our new engineer doesn't yet have a way to log in to the AWS account. You shouldn’t share your credentials, especially if you have access to production resources!

Let’s create:

- A dedicated **IAM group** for XYZ Engineers  
- A dedicated **IAM user** for the new engineer

#### Create a User Group

1. Go to **User groups** from the left-hand navigation panel  
2. Click **Create group**  
3. Set:  
   - **Name**: `XYZ-dev-group`  
   - **Attached policy**: `XYZDevEnvironmentPolicy`  
4. Click **Create group** — ✅ Success!

#### Create a User

1. Go to **Users > Create user**  
2. Enter **User name**: `XYZ-dev-name`  
3. Check **Provide user access to the AWS Management Console**  
4. Uncheck **Users must create a new password at next sign-in**

> ⚠️ If prompted: *"Are you providing console access to a person?"* — select **I want to create an IAM user**

5. Click **Next**  
6. Select the checkbox next to `XYZ-dev-group`  
7. Click **Next**, then **Create user**

✅ The user is created! You’ll now see their sign-in details. Stay on this page.

---

### 5. Test Your Engineer's Access

> 🧪 Before sharing login info, let’s test the engineer's IAM user permissions.

1. Copy the **Console sign-in URL** (from the IAM user page)  
2. Open the link in an **incognito window**  
3. Log in with the IAM username and password  
4. Go to the **EC2 Console** — be sure you're in the correct Region  
5. Try the following:

#### ❌ Attempt to stop the **Production** instance:
- Go to **Instances**
- Select the production instance
- Under **Actions > Manage instance state**, click **Stop**
- ✅ Should be **denied**

#### ✅ Attempt to stop the **Development** instance:
- Select the `XYZ-dev-name` instance
- Under **Actions > Manage instance state**, click **Stop**
- ✅ Should be **allowed**

🎉 Success! IAM permissions are working as expected.

---

### 6. Delete Your Resources

Once done, clean up everything:

#### EC2 Console:
- Terminate both **development** and **production** instances  
- 💡 Tip: Click the **"x"** next to `Instance state = running` filter to see all instances

#### IAM Console:
- Delete the **User group**: `XYZ-dev-group`  
- Delete the **User**: `XYZ-dev-name`  
- Delete the **Policy**: `XYZDevEnvironmentPolicy`

6. Click **Next**
7. Fill in the policy details:
   - **Name**: `XYZDevEnvironmentPolicy`
   - **Description**: IAM Policy for NextWorks development environment
8. Click **Create policy**

✅ Awesome, the permission policy is all set up!  
Now that our engineer has access to the development instance, they’re excited and ready to dive in.

---

### 3. Create an AWS Account Alias

1. Head to your **IAM dashboard**
2. On the right-hand side, choose **Create** under **Account Alias**
3. In the **Preferred alias** field, enter: `XYZ-alias-name`
4. Click **Create alias**

---

### 4. Create IAM Users and User Groups

> 📝 **Note:** Our new engineer doesn't yet have a way to log in to the AWS account. You shouldn’t share your credentials, especially if you have access to production resources!

Let’s create:

- A dedicated **IAM group** for XYZ Engineers
- A dedicated **IAM user** for the new engineer

#### Create a User Group

1. Go to **User groups** from the left-hand navigation panel
2. Click **Create group**
3. Set:
   - **Name**: `XYZ-dev-group`
   - **Attached policy**: `XYZDevEnvironmentPolicy`
4. Click **Create group** — ✅ Success!

#### Create a User

1. Go to **Users > Create user**
2. Enter **User name**: `XYZ-dev-name`
3. Check **Provide user access to the AWS Management Console**
4. Uncheck **Users must create a new password at next sign-in**

> ⚠️ If prompted: *"Are you providing console access to a person?"* — select **I want to create an IAM user**

5. Click **Next**
6. Select the checkbox next to `XYZ-dev-group`
7. Click **Next**, then **Create user**

✅ The user is created! You’ll now see their sign-in details. Stay on this page.

---

### 5. Test Your Engineer's Access

> 🧪 Before sharing login info, let’s test the engineer's IAM user permissions.

1. Copy the **Console sign-in URL** (from the IAM user page)
2. Open the link in an **incognito window**
3. Log in with the IAM username and password
4. Go to the **EC2 Console** — be sure you're in the correct Region
5. Try the following:

#### ❌ Attempt to stop the **Production** instance:
- Go to **Instances**
- Select the production instance
- Under **Actions > Manage instance state**, click **Stop**
- ✅ Should be **denied**

#### ✅ Attempt to stop the **Development** instance:
- Select the `XYZ-dev-name` instance
- Under **Actions > Manage instance state**, click **Stop**
- ✅ Should be **allowed**

🎉 Success! IAM permissions are working as expected.

---

### 6. Delete Your Resources

Once done, clean up everything:

#### EC2 Console:
- Terminate both **development** and **production** instances  
- 💡 Tip: Click the **"x"** next to `Instance state = running` filter to see all instances

#### IAM Console:
- Delete the **User group**: `XYZ-dev-group`
- Delete the **User**: `XYZ-dev-name`
- Delete the **Policy**: `XYZDevEnvironmentPolicy`
