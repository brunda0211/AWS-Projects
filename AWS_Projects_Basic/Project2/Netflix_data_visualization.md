# 📊 Netflix Data Visualization: Amazon QuickSight + S3 Setup

## 🧭 Introduction

In this project, you're stepping into the role of a Data Enthusiast at **XYZ**, analyzing Netflix's vast catalogue of shows and movies. Your task is to build a dynamic and interactive **dashboard using Amazon QuickSight**, powered by data stored in **Amazon S3**.

You'll visualize trends like release years, genres, and content types — all in a way that helps teams extract insights and make data-driven decisions.

No prior experience with data tools? No worries. This guide is beginner-friendly and designed to help you learn while doing.

---

## 💰 Cost

**FREE** (Amazon QuickSight offers a free trial and Amazon S3 has a free tier)

---

## 🎯 Objectives

To complete this project, you will:

- 🪣 Create and configure an Amazon S3 bucket
- 📂 Upload and structure a Netflix dataset with a `manifest.json` file
- 🆕 Set up a **QuickSight** account
- 🔗 Connect QuickSight to your S3 data source
- 📊 Build visualizations and dashboards in QuickSight
- 🧹 Clean up resources after completion

---

## ⚠️ Heads Up! Before You Begin...

### 💡 What is Amazon S3?

Amazon S3 is a storage service where you can host files like CSVs and JSONs in the cloud. In this project, your Netflix data will live in an S3 bucket.

### 💡 What is Amazon QuickSight?

Amazon QuickSight is a business intelligence (BI) tool that lets you connect to data sources, analyze them, and create visual dashboards with charts, tables, and more.

### 📄 What is a Manifest File?

The `manifest.json` file tells QuickSight how to interpret and access the dataset in your S3 bucket. It defines the structure and location of your data.

---

## 🔧 Step-by-Step Implementation

### 1. Upload Dataset to S3

1. Download the following:
   - `netflix_titles.csv`
   - `manifest.json`

2. Log in to your AWS Console and navigate to **S3**.
3. Create a bucket named:  
   `XYZ-quicksight-project-<your-name>`

4. Upload both files to your bucket.

5. Open the `manifest.json` file locally and replace the S3 URL placeholder with your actual S3 path:
   ```json
   "s3://xyz-quicksight-project-<your-name>/netflix_titles.csv"
   ```

6. Save and re-upload the modified `manifest.json` file into the same S3 bucket, replacing the old one.

✅ **At this point, your S3 bucket should contain both the dataset and manifest file.**

---

### 2. Set Up QuickSight Account

1. From the AWS Console, search and open **QuickSight**.
2. Sign up for the **free Enterprise trial**.
3. Use the **same email address** as your AWS account.
4. Set the region to match your S3 bucket's region. 
5. Add a QuickSight account name: XYZ-QuickSight-enter your name
6. Enable access to **Amazon S3**, then **select the bucket** you created.
7. Uncheck **Paginated Reports** to avoid charges.
8. Click **Finish** to complete setup.

✅ QuickSight account successfully created!

---

### 3. Connect S3 Data to QuickSight

1. In QuickSight, go to the **Datasets** panel.
2. Select **New dataset > S3**.
3. Set:
   - **Name**: `kaggle-netflix-data`
   - **Manifest URL**: paste your S3 URL to `manifest.json`

4. Click **Connect**
5. On success, select **Visualize** to launch the analysis tool.

---

### 4. Create Your First Visualizations

1. From the field list, drag `release_year` into the analysis pane to create a **bar chart**.
2. Switch chart types to **donut** or **line** for fun experimentation.
3. Add another visualization:
   - Drag `release_year` to Y-axis
   - Drag `type` to Group/Color

4. Resize and rearrange visualizations on the canvas.

✅ You've now built your first QuickSight dashboard!

---

### 5. Answer Real Questions with Visuals

Using QuickSight, create visualizations to answer these:

- What's the distribution of **TV shows vs Movies** over the years?
- Which **genres** are most popular?
- How many titles were **added each year**?
- What does the distribution of shows by **country** look like?

Use **filters, stacked bar charts, pie charts**, and **tables** to explore!

---

### 6. Publish and Share Your Dashboard

1. Add clear, descriptive **titles** to each visualization.
2. Click **Publish** in the top right corner.
3. Name your dashboard (e.g., *Netflix Titles Analysis*).
4. Click the **Export** icon to save your dashboard as a **PDF**.

✅ Your visual insights are now ready to be shared!

---

### 7. Clean Up Resources

To avoid charges, delete:

- Your **QuickSight account**
- Your **S3 bucket and uploaded files**

From AWS Console:
- Navigate to **S3** → delete your bucket
- Go to **QuickSight settings** → unsubscribe from service

---

## 🏆 What You’ve Achieved

- Mastered S3 bucket setup and file management
- Connected datasets to QuickSight with manifest files
- Created rich visualizations with filters, groupings, and multiple charts
- Built and published a professional-looking dashboard
