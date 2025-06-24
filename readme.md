# AWS Solutions: A Portfolio of Cloud Projects ☁️
Welcome to my AWS Project Portfolio! This repository showcases a range of projects that highlight the use of various AWS services and solutions, providing hands-on experience from basic concepts to advanced cloud architectures.
### Project Levels
The projects are categorized into four levels, each reflecting a different degree of expertise:
* <a href ="https://github.com/brunda0211/AWS-Projects/tree/main/AWS_Projects_Basic">Level 1 (Basic)</a>
* <a href ="https://github.com/brunda0211/AWS-Projects/tree/main/AWS_Projects_Intermediate">Level 2 (Intermediate)</a>
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


### **Project 4: Host a Static Website on Amazon S3**

- **Description**: In this project, we’ll host a static website using Amazon S3. You’ll create an S3 bucket, upload HTML and image files, configure static website hosting, and make the files publicly accessible. This project is part of the AWS Beginner Challenge and introduces key concepts like ACLs, bucket policies, and static hosting.

- **Service Used**: Amazon S3

- **Link**: [Project Directory](https://github.com/brunda0211/AWS-Projects-Portfolio/blob/main/AWS_Projects_Basic/Host%20a%20website%20on%20Amazon%20S3/Host%20a%20website%20on%20Amazon%20S3.md)


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

### Project 5: Automated S3 Setup with Terraform

- **Description**: This project demonstrates how to provision an Amazon S3 bucket and upload a local image file using Infrastructure as Code (IaC) with Terraform. It covers setting up Terraform on macOS, configuring AWS credentials via AWS CLI, and writing Terraform configuration files to create an S3 bucket with public access blocked. You'll also upload a file to the bucket and destroy the infrastructure afterward. This beginner-friendly project highlights core IaC practices and cloud resource automation.

- **Service Used**: AWS S3, AWS IAM, AWS CLI,Terraform (Infrastructure as Code)

- **Link**: [Project Directory](https://github.com/brunda0211/AWS-Projects/blob/main/AWS_Projects_Intermediate/Create%20S3%20buckets%20using%20Terraform/Create%20S3%20bucket%20using%20terraform.md#-create-an-s3-bucket-and-upload-files-using-terraform)



### Project 6: CI/CD-Based IAM Group Assignment Using Terraform

- **Description**: This project simulates a real-world corporate workflow where IAM user and group management is handled using Terraform. Changes are made through Git branches and Pull Requests, with a CI/CD pipeline. A ticket-based task is resolved by modifying shared Terraform files to add a new IAM user to a group. This project emphasizes Infrastructure as Code (IaC), collaboration using Git, and automation using CI/CD practices like GitHub Actions. 

- **Services Used**: AWS IAM, Terraform, GitHub, GitHub Actions

- **Link**: [Project Directory](https://github.com/brunda0211/AWS-Projects-Portfolio/blob/main/AWS_Projects_Intermediate/CI/CD-Based%20IAM%20Group%20Assignment%20Using%20Terraform/CI%20CD-Based%20IAM%20Group%20Assignment%20Using%20Terraform.md)

### Project 7: RAG Chatbot with AWS Bedrock

- **Description**: This project demonstrates how to build a document-powered chatbot using AWS Bedrock's Retrieval-Augmented Generation (RAG) system. You'll create a Knowledge Base with OpenSearch vector storage, connect document sources from S3, and configure Meta's Llama 3 models for natural conversations. Learn to process documents with Titan embeddings, handle sync operations, and test domain-specific responses while filtering out-of-context queries. Perfect for understanding enterprise-grade AI implementations.

- **Services Used**: Amazon Bedrock, Amazon S3, OpenSearch Serverless, AWS IAM, Meta Llama 3 (8B & 70B Instruct), Titan Text Embeddings

- **Link**: [Project Directory](https://github.com/brunda0211/AWS-Projects-Portfolio/blob/main/AWS_Projects_Intermediate/Build%20a%20RAG-Powered%20Chatbot%20with%20AWS%20Bedrock/Build%20a%20RAG-Powered%20Chatbot%20with%20AWS%20Bedrock.md)

## Level 3 (Advanced Projects)

These projects are the most challenging, demonstrating advanced AWS solutions and best practices. 


### Project 1 : Create a Continuous Delivery Pipeline 

  - **Description**: This project implements a Continuous Delivery (CD) pipeline using AWS CodePipeline, AWS CodeBuild, and AWS Elastic Beanstalk to automate deployments. The setup provides a structured approach to code deployment, enhancing reliability and minimizing manual processes—ideal for agile development teams aiming for efficient, high-frequency deployments.


  - **Service Used**: AWS CodePipeline, AWS CodeBuild, AWS Elastic Beanstalk, Amazon EC2 with Auto Scaling

  - **Link**: [Project Directory](https://github.com/brunda0211/AWS-Projects/blob/main/AWS_Projects_Advanced/Create%20a%20Continuous%20Delivery%20Pipeline/Create%20a%20Continuous%20Delivery%20Pipeline.md) 


  ### Project 2 : Build a Serverless Web Application using Generative AI

  - **Description**: This project walks through creating a serverless recipe generator application using AWS Amplify and Amazon Bedrock. Users can input ingredients and receive AI-generated recipes via a simple web interface. By combining Generative AI with a serverless architecture, this application offers a scalable and interactive experience.


  - **Service Used**: AWS Amplify, Amazon Bedrock, AWS AppSync, AWS Cognito, AWS Lambda, Node.js

  - **Link**: [Project Directory](https://github.com/brunda0211/AWS-Projects-Portfolio/blob/main/AWS_Projects_Advanced/Build%20a%20Serverless%20Web%20Application%20using%20Generative%20AI/Build%20a%20serverless%20web%20app.md) 