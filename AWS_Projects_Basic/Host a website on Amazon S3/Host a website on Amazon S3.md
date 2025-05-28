# 🌐 Host a Website on Amazon S3

## 🧭 Introduction
Let’s host your very own website on **Amazon S3**!  
You’ll use S3 (Simple Storage Service) to create a public-facing static website by uploading files and configuring permissions.

---

## 💰 Cost
**$0** (Eligible under AWS Free Tier)

---

## 🎯 Objectives
- 🪣 Create an Amazon S3 Bucket  
- 📁 Upload HTML and image files  
- 🌐 Configure static website hosting  
- 🔓 Make objects publicly accessible  
- 🧼 Delete all resources at the end  

---

## ⚠️ Prerequisites
- An AWS Account – [Create one here](https://aws.amazon.com/free)

---

## ⚒️ Key Concepts

### Amazon S3
A storage service that allows you to store and retrieve data over the internet.

### Hosting a Website
Hosting means making your content publicly accessible online.

### ACL (Access Control List)
Defines permissions for who can access specific objects within S3.

### Static Website Hosting
Amazon S3 can host websites composed of HTML and image files.

---

## 🪣 Step 1: Create an S3 Bucket

1. Log in to your AWS console  
2. Search for **S3**  
3. Click **Create bucket**  
4. Bucket name: `XYZ-website-project-YOURNAME`  
5. Select your nearest AWS **Region**  
6. Object Ownership: **ACLs enabled**  
7. Block Public Access: **Unchecked** (acknowledge warning)  
8. Bucket Versioning: **Enabled**  
9. Click **Create bucket**

> 💡 S3 bucket names are globally unique. Replace `YOURNAME` with your name to avoid conflicts.

---

## 📁 Step 2: Upload Website Content

1. Open your bucket  
2. Download and unzip these files:  
   - `index.html`  
   - `XYZ - Everyone...love_files.zip`  
3. Go to **Objects** tab > click **Upload**  
4. Add `index.html` and the unzipped folder  
5. Click **Upload**

> 💡 HTML (HyperText Markup Language) builds your web pages.

---

## 🌐 Step 3: Enable Static Website Hosting

1. Go to the **Properties** tab of your bucket  
2. Scroll to **Static website hosting** > click **Edit**  
3. Enable Static hosting  
4. Hosting type: `Host a static website`  
5. Index document: `index.html`  
6. Save changes  
7. Copy the **Bucket website endpoint** URL

> 💡 If you see an error, your files are still private. Proceed to the next step.

---

## 🔓 Step 4: Make Objects Public

1. Go to the **Objects** tab  
2. Select `index.html` and the image folder files  
3. Click **Actions > Make public using ACL**

Now reload your website URL — your static site should be live 🎉

---

## 🗑️ Delete Resources

To avoid charges, delete:

- All **S3 objects**
- The **S3 bucket**
