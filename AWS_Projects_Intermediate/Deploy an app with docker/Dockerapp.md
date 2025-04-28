# 🚀 Deploy an App with Docker and AWS Elastic Beanstalk

---

## 🧭 Introduction

In this project, we'll install Docker, create and run a custom container locally, and deploy the containerized application using AWS Elastic Beanstalk to make it live on the web!

You'll learn how to:
- Install and use Docker
- Build and run custom container images
- Deploy containerized applications to the cloud

---

## 💰 Cost

**FREE** (Eligible under AWS Free Tier)

---

## 🎯 Objectives

To:
- 🐳 Install Docker
- 🖼️ Build a custom container image
- 🚢 Run a container locally
- ☁️ Deploy the container to AWS Elastic Beanstalk

---

## ⚠️ Before You Begin

### 🔐 What is Docker?
Docker is a tool that allows you to package applications and their dependencies into containers for fast and consistent deployment.

### 📦 What are Containers?
Containers are lightweight, portable packages of software that include everything needed to run an application.

### 🌱 What is AWS Elastic Beanstalk?
Elastic Beanstalk makes it easy to deploy and manage applications in the AWS cloud without worrying about infrastructure.

---

## 🔧 Step-by-Step Implementation

---

### 1. Install Docker

- Download Docker Desktop from the [official website](https://www.docker.com/products/docker-desktop/).
- Install Docker according to your OS (Mac, Windows, Linux).
- Open Docker Desktop and skip sign-in (optional).

Verify installation:
```bash
docker --version
```
You should see the Docker version printed.

✅ Docker and Docker daemon running confirmed!

---

### 2. Run a Pre-Built Container (Nginx)

- Open your terminal.
- Run the command:
```bash
docker run -d -p 80:80 nginx
```
- Open your browser and navigate to `http://localhost` — you should see the Nginx welcome page!

✅ Successfully launched a container locally!

---

### 3. Build Your Custom Container Image

- Create a folder called `Compute` on your Desktop.

- Create a `Dockerfile` with the following content:
```dockerfile
FROM nginx:latest
COPY index.html /usr/share/nginx/html/
EXPOSE 80
```

- Create an `index.html` file in the same folder with:
```html
<!doctype html>
<html>
  <head>
    <title>My Web App</title>
  </head>
  <body>
    <h1>Hello from YOURNAME's custom Docker image!</h1>
  </body>
</html>
```

✅ Dockerfile and index.html ready!

- Build your Docker image:
```bash
cd ~/Desktop/Compute
docker build -t my-web-app .
```

✅ Custom Docker image built!

---

### 4. Run Your Custom Image

- Run your container:
```bash
docker run -d -p 80:80 my-web-app
```

- If port conflict error occurs:
  - Stop the existing container.
  - Retry the `docker run` command.

- Navigate to `http://localhost` and see your custom web page!

✅ Custom container running locally!

---

### 5. Log in to AWS with IAM User

- Create an IAM User with **AdministratorAccess** permissions.
- Download credentials and sign in using your IAM user credentials.

✅ AWS access ready!

---

### 6. Deploy the Container to AWS Elastic Beanstalk

#### Create and Upload Application

- Search **Elastic Beanstalk** in AWS Console.
- Click **Create Application**.
- Application name: `YourName App`
- Platform: **Docker**
- Create a ZIP file containing only `Dockerfile` and `index.html`.
- Upload your ZIP file as the application code.
- Choose **Single Instance (Free tier eligible)** preset.

#### Configure Access

- Create a new service role automatically.
- Instance Profile: Select `ecsInstanceRole`.

#### Configure Networking

- Activate **Public IP Address** under instance settings.

#### Configure Storage

- Root Volume Type: `gp3`
- Size: `10 GB`

#### Configure Monitoring

- System Monitoring: **Basic** (important for Free Tier eligibility)

#### Final Review Checklist

✅ Application Name: NextWork App  
✅ Public IP Enabled  
✅ Instance Type: Single Instance  
✅ Root Volume: gp3  
✅ System Monitoring: Basic  
✅ Managed Updates: Deactivated  
✅ Deployment Policy: AllAtOnce

Submit to launch environment 🚀

✅ Environment successfully deployed!

---

## 🌍 View Your Application

- On the Elastic Beanstalk Dashboard, click on the **Domain link**.
- You should see your custom web page live on the internet!

---

# 🎉 Congratulations!
You have successfully:
- Installed Docker
- Built and ran a custom container locally
- Deployed your containerized app using AWS Elastic Beanstalk
- Accessed your live application on the web! 🚀

---

# 🧹 Clean Up (Optional)

- Terminate your Elastic Beanstalk environment.
- Delete the application from Elastic Beanstalk.
- Remove any unnecessary Docker containers and images locally.

✅ Done!
