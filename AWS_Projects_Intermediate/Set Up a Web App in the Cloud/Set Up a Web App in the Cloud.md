# Set Up a Web App in the Cloud

## 🔍 Introduction
 This beginner-friendly project walks you through the foundational DevOps setup: launching a web app on AWS using EC2 and connecting through VS Code.

You'll:
- 💻 Launch an EC2 instance
- 🔐 Set up secure SSH access
- 🛠 Install Maven and Java (Amazon Corretto 8)
- ✍️ Generate and edit a Java web app
- 🔗 Connect VS Code directly to your EC2 instance

This project kicks off the creation of a complete CI/CD pipeline. You'll build the base environment here and expand on it in later challenges.

---

## 💰 Cost
FREE (Eligible under AWS Free Tier)

---

## 🎯 Objectives
To create:
- EC2 instance with secure access
- Maven-based Java web app
- Remote editing via VS Code

---

## ⚠️ Heads Up! Before You Begin...

### 🔐 What is AWS IAM?
AWS IAM (Identity and Access Management) helps manage who can access AWS resources and what actions they can perform. Use IAM instead of your root account for better security.

### 🖥 What is EC2?
EC2 (Elastic Compute Cloud) provides virtual machines in the cloud. You can use EC2 instances for app development, hosting, and testing.

### 🔑 What is a Key Pair?
A key pair allows secure login to your EC2 instance. AWS stores the public key; you use the downloaded private key (.pem file).

### ⚙️ What is VS Code?
Visual Studio Code is an IDE used to write, edit, and manage code. It supports extensions like Remote - SSH for server access.

---

## 🧑‍💻 Step-by-Step Implementation

### 1. Set Up IAM User
- Log in as root user
- Navigate to IAM > Users > Create User
- Name: `YourName-IAM-Admin`
- Enable console access with custom password
- Attach policy: `AdministratorAccess`
- Create user and download `.csv` with credentials
- Log out and log in as new IAM user

### 2. Launch EC2 Instance
- Go to EC2 > Instances > Launch instance
- Name: `nextwork-devops-yourname`
- AMI: Amazon Linux 2023
- Type: `t2.micro`
- Create new key pair: `nextwork-keypair.pem`
- Set network: Allow SSH from My IP
- Launch instance

### 3. Configure Your Local Machine
- Move `.pem` file to `~/Desktop/DevOps/`
- Open VS Code > Terminal > `cd ~/Desktop/DevOps`
- Run `chmod 400 nextwork-keypair.pem`

### 4. Connect via SSH
- Get Public IPv4 DNS from EC2 instance
- SSH into instance:
```bash
ssh -i ~/Desktop/DevOps/nextwork-keypair.pem ec2-user@<Your-Public-DNS>
```
- Accept fingerprint and connect

### 5. Install Maven and Java

#### 🛠 Fix for wget not found error:
```bash
sudo yum install wget -y
```

#### 📦 Install Apache Maven:
```bash
wget https://archive.apache.org/dist/maven/maven-3/3.5.2/binaries/apache-maven-3.5.2-bin.tar.gz
sudo tar -xzf apache-maven-3.5.2-bin.tar.gz -C /opt
echo "export PATH=/opt/apache-maven-3.5.2/bin:$PATH" >> ~/.bashrc
source ~/.bashrc
```

#### ☕ Install Amazon Corretto 8 (Java 8):
```bash
sudo dnf install -y java-1.8.0-amazon-corretto-devel
export JAVA_HOME=/usr/lib/jvm/java-1.8.0-amazon-corretto.x86_64
export PATH=/usr/lib/jvm/java-1.8.0-amazon-corretto.x86_64/jre/bin/:$PATH
```

- Verify:
```bash
mvn -v
java -version
```

### 6. Generate Java Web App
```bash
mvn archetype:generate \
   -DgroupId=com.nextwork.app \
   -DartifactId=nextwork-web-project \
   -DarchetypeArtifactId=maven-archetype-webapp \
   -DinteractiveMode=false
```

### 7. Connect VS Code with EC2 Instance
- Install Remote - SSH extension in VS Code
- Open terminal in VS Code, run:
```bash
ssh -i ~/Desktop/DevOps/nextwork-keypair.pem ec2-user@<Your-Public-DNS>
```
- Use the bottom-left remote explorer icon to add new SSH Host
- Add path to `.pem` and connect
- Open folder: `/home/ec2-user/nextwork-web-project`

### 8. Edit Web App

- In VS Code, go to the Extensions icon in the sidebar.
- Search for **Remote - SSH** and click **Install**.

💡 **Why install Remote - SSH?**
Remote - SSH allows you to securely connect to remote machines (like your EC2 instance) and work on them directly from VS Code with all the benefits of an IDE.

- Click the double arrow icon in the bottom-left corner of VS Code.
- Select **Connect to Host...** > **+ Add New SSH Host...**
- Paste the following command:
  ```bash
  ssh -i ~/Desktop/DevOps/nextwork-keypair.pem ec2-user@<Your-Public-DNS>
  ```
- Select your SSH config file (e.g., `/Users/username/.ssh/config`) and confirm the details:
  - `Host` should be your EC2 DNS
  - `IdentityFile` path should be correct
  - `User` should be `ec2-user`
- Save and connect to the EC2 instance.
- Once connected, go to the **Explorer** icon in the sidebar and click **Open Folder**.
- Type in `/home/ec2-user/nextwork-web-project` and press OK.
- If prompted, select **Yes, I trust the authors**.
- Expand all folders to view your Maven-generated project structure:
  - `src/main/webapp`: contains HTML, JSP, and frontend resources
  - `src/main/resources`: configuration files
  - `pom.xml`: Maven configuration file

- Open `index.jsp` in the `webapp` folder.
- Replace its content with:
  ```html
  <html>
  <body>
  <h2>Hello {Your Name}!</h2>
  <p>This is my NextWork web application working!</p>
  </body>
  </html>
  ```
- Save the file using `Cmd/Ctrl + S`.

💡 **What is index.jsp?**
This is a Java Server Page — similar to HTML but capable of including Java code to create dynamic web content.

Congrats — you just edited your live web app using VS Code connected to an EC2 instance!---

## 🧹 Delete Your Resources
### EC2 Console:
- Terminate EC2 instance

### Optional:
- Delete key pair under EC2 > Key Pairs

---

## ✅ Success!
You’ve just built a Java web app inside an EC2 instance, secured it with a key pair, and edited your code using VS Code. Great foundation for future CI/CD projects!
