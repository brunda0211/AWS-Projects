# 🚀 Build a Virtual Private Cloud (VPC) on AWS

---

## 🧭 Introduction

In this project, we'll set up a custom Virtual Private Cloud (VPC) from scratch inside AWS.  
Think of it like building your own private city in the cloud — dividing it into neighborhoods (subnets) and linking it to the outside world (internet gateway).

You'll learn how to:
- Create a VPC
- Set up a public subnet
- Attach an internet gateway for external connectivity

---

## 💰 Cost

**FREE** (Eligible under AWS Free Tier)

---

## 🎯 Objectives

To create:
- ☁️ Amazon VPC
- 🏘️ Public Subnet
- 🌐 Internet Gateway

---

## ⚠️ Heads Up! Before You Begin

### 🔐 What is a VPC?
A Virtual Private Cloud (VPC) is a private section of AWS where you can launch AWS resources in a logically isolated network.

### 🏘️ What is a Subnet?
A subnet is a subdivision within your VPC where you can place resources according to different access rules — like public-facing servers or private databases.

### 📡 What is an Internet Gateway?
An Internet Gateway connects your private VPC to the broader internet, enabling resources like EC2 instances to communicate externally.

---

## 🔧 Step-by-Step Implementation

---

### 1. Create a VPC

- Log in to the AWS Management Console.
- Search for **VPC** in the search bar.
- In the left navigation pane, select **Your VPCs**.
- Click **Create VPC**.
- Choose **VPC Only** option.
- Set:
  - **Name tag:** `XYZ VPC`
  - **IPv4 CIDR block:** `10.0.0.0/16`
- Take a screenshot of your setup page.
- Click **Create VPC**.

✅ Your VPC is ready!

---

### 2. Create a Public Subnet

- In the VPC Dashboard, choose **Subnets** from the left menu.
- Click **Create Subnet**.
- Fill:
  - **VPC ID:** `XYZ VPC`
  - **Subnet name:** `Public 1`
  - **Availability Zone:** Choose the first AZ available.
  - **IPv4 CIDR block:** `10.0.0.0/24`
- Click **Create Subnet**.

#### 🛠 Enable Auto-Assign Public IP

- Select the checkbox next to `Public 1`.
- Click **Actions** > **Edit subnet settings**.
- Check **Enable auto-assign public IPv4 address**.
- Save the changes.

🧠 **Note:**  
Auto-assigning public IP addresses ensures instances in this subnet can be accessed via the internet.

---

### 3. Create and Attach an Internet Gateway

- In the left menu, click **Internet Gateways**.
- Click **Create Internet Gateway**.
- Set:
  - **Name tag:** `XYZ IG`
- Click **Create Internet Gateway**.

#### 🔗 Attach the Internet Gateway to VPC

- Select `XYZ IG`.
- Click **Actions** > **Attach to VPC**.
- Choose `XYZ VPC`.
- Click **Attach Internet Gateway**.

🧠 **Note:**  
Now, your VPC can communicate with the internet through the attached Internet Gateway.

---

## 🧹 Clean Up (Optional)

To avoid any AWS charges:
- **Terminate** instances (if created later).
- **Detach and delete** the Internet Gateway.
- **Delete** the Subnet.
- **Delete** the VPC.

---

# 🎉 Congratulations!

You successfully built a Virtual Private Cloud on AWS — organized it into a public subnet and linked it to the internet! 🚀
