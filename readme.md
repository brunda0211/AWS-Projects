# AWS Solutions: A Portfolio of Cloud Projects ☁️
Welcome to my AWS Project Portfolio! This repository showcases a range of projects that highlight the use of various AWS services and solutions, providing hands-on experience from basic concepts to advanced cloud architectures.
### Project Levels
The projects are categorized into four levels, each reflecting a different degree of expertise:
* <a href ="https://github.com/brunda0211/AWS-Projects/tree/main/AWS_Projects_Basic/Project1%20">Level 1 (Basic)</a>
* <a href ="">Level 2 (Intermediate)</a>
* <a href ="">Level 3 (Advanced)</a>
## Level 1 (Basic Projects)

This section features projects ideal for beginners, focusing on fundamental AWS concepts and basic services.

### **Project 1 : DevOps Engineer Onboarding: EC2 + IAM Setup**

  - **Description**: In this project, we’ll launch an EC2 instance, and then use IAM policies, user groups, and an AWS Account Alias to control access. The policy we create will grant full access only to EC2 instances tagged with ENV: development

  - **Service Used**: AWS IAM, EC2
  
  - **Link**: [Project Directory](https://github.com/brunda0211/AWS-Projects/blob/main/AWS_Projects_Basic/Engineer%20Onboarding%3A%20EC2%20%2B%20IAM%20Setup/IAM_EC2_Policy_Steps.md)

### **Project 2: Netflix Data Visualization with Amazon QuickSight + S3**

- **Description:** In this project, we’ll analyze Netflix’s global catalogue using AWS. You’ll upload a dataset to Amazon S3, connect it to Amazon QuickSight via a manifest file, and build an interactive dashboard to visualize trends across years, genres, and content types.

- **Service Used:** Amazon S3, Amazon QuickSight

- **Link:** [Project Directory](https://github.com/brunda0211/AWS-Projects/blob/main/AWS_Projects_Basic/%20Netflix%20Data%20Visualization%3A%20Amazon%20QuickSight%20%2B%20S3%20Setup/Netflix_data_visualization.md)

###  Project 3: Build a Virtual Private Cloud (VPC) on AWS

- **Description**: In this project, we’ll build a Virtual Private Cloud (VPC) inside AWS, create a public subnet, and connect it to the internet using an Internet Gateway. This sets up the foundation for secure and scalable AWS networking.
  
- **Service Used**: Amazon VPC

- **Link**: [Project Directory](https://github.com/brunda0211/AWS-Projects/blob/main/AWS_Projects_Basic/Build%20a%20VPC/vpc.md)


## Level 2 (Intermediate Projects)

This section features projects that involve combining multiple AWS services, handling user data, and implementing logic flows. These projects are ideal for learners who understand the basics and want to build more interactive and real-world cloud applications.


### **Project 1 : BankerBot - A Conversational AI Chatbot using Amazon Lex**

  - **Description**: This project walks through building a fully functional banking chatbot using Amazon Lex and Lambda. The bot handles greetings, balance checks, context-based follow-ups, and fund transfers using custom slots and confirmation prompts. You’ll also automate deployment using AWS CloudFormation and explore Lex’s visual tools.

  - **Service Used**: Amazon Lex, AWS Lambda, CloudFormation. 

  - **Link**: [Project Directory](https://github.com/brunda0211/AWS-Projects/blob/main/AWS_Projects_Intermediate/Bankerbot%20-%20Chatbot%20with%20Amazon%20Lex/Chatbot_using_lex.md)


### Project 2 : Multi-Cloud Data Transfer with AWS and GCP

- **Description**: This project demonstrates how to transfer data securely between AWS S3 and Google Cloud Storage using GCP’s Storage Transfer Service. You'll configure identity federation via IAM roles, set up cloud storage buckets on both platforms, and execute a batch transfer job. Optionally, you can filter transfers using a manifest file. This project is ideal for practicing cross-cloud architecture and automation skills.

- **Service Used**: AWS S3, AWS IAM, Google Cloud Storage, GCP Storage Transfer Service 

- **Link**: [Project Directory](https://github.com/brunda0211/AWS-Projects/blob/main/AWS_Projects_Intermediate/GCP%20and%20AWS%20Multi-Cloud%20Data%20Transfer/Multi-Cloud-Data-Transfer-Project.md)

### Project 3 : Deploy an App with Docker and AWS Elastic Beanstalk

- **Description**: This project walks through installing Docker, creating a custom container image, running it locally, and deploying the containerized application to AWS Elastic Beanstalk. You'll make your web application live on the internet, while learning containerization and cloud deployment fundamentals.

- **Service Used**: Docker, AWS Elastic Beanstalk

- **Link**: [Project Directory](https://github.com/brunda0211/AWS-Projects/blob/main/AWS_Projects_Intermediate/Deploy%20an%20app%20with%20docker/Dockerapp.md)


### Project 4 : Set Up a Web App in the Cloud

- **Description**: This project walks you through the steps to launch a Java-based web application on an Amazon EC2 instance and connect to it securely using SSH and Visual Studio Code. You'll install Maven and Amazon Corretto 8, generate a web app, and edit project files directly on the remote server using the Remote - SSH extension in VS Code. This project serves as the foundation for building a complete CI/CD pipeline in the following challenges.

- **Service Used**: Amazon EC2, AWS IAM, Apache Maven, Amazon Corretto, Visual Studio Code (Remote - SSH)

- **Link**: [Project Directory](https://github.com/brunda0211/AWS-Projects/blob/main/AWS_Projects_Intermediate/Set%20Up%20a%20Web%20App%20in%20the%20Cloud/Set%20Up%20a%20Web%20App%20in%20the%20Cloud.md) 

## Project 5: Automated S3 Setup with Terraform

### 📌 Description
This project demonstrates how to provision an Amazon S3 bucket and upload a local image file using Infrastructure as Code (IaC) with Terraform. It covers setting up Terraform on macOS, configuring AWS credentials via AWS CLI, and writing Terraform configuration files to create an S3 bucket with public access blocked. You'll also upload a file to the bucket and destroy the infrastructure afterward. This beginner-friendly project highlights core IaC practices and cloud resource automation.

- **Service Used**: AWS S3, AWS IAM, AWS CLI,Terraform (Infrastructure as Code)

### 🔗 Link
[Project Directory](https://github.com/brunda0211/AWS-Projects/blob/main/AWS_Projects_Intermediate/Create%20S3%20buckets%20using%20Terraform/Create%20S3%20bucket%20using%20terraform.md#-create-an-s3-bucket-and-upload-files-using-terraform)


