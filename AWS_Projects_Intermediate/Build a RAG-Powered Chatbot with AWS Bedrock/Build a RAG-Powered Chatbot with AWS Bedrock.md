# 🚀 Build a RAG-Powered Chatbot with AWS Bedrock

---

## 🧭 Introduction

In this project, we'll create an AI chatbot that answers questions using your own documents through AWS Bedrock's Retrieval-Augmented Generation (RAG) system.  
Think of it like training a personal research assistant that only knows what's in your files.

You'll learn how to:
- Create a Knowledge Base
- Connect documents from S3
- Choose between Llama 3 AI models
- Test domain-specific responses

---

## 💰 Cost

**~$0.10 total** (Mostly free-tier eligible, minimal Bedrock usage fees)

---

## 🎯 Objectives

To create:
- ☁️ Amazon Bedrock Knowledge Base
- 📦 S3 Document Storage
- 🤖 Llama 3 AI Chatbot
- 🔍 OpenSearch Vector Store

---

## ⚠️ Heads Up! Before You Begin

### 🔐 What is RAG?
Retrieval-Augmented Generation combines document search with AI - first finding relevant info, then generating answers.

### 🏘️ What is a Knowledge Base?
Your chatbot's "brain" - where processed documents are stored for quick retrieval.

### 📡 What is OpenSearch Serverless?
The search engine that helps your chatbot understand questions contextually, not just keyword-matching.

---

## 🔧 Step-by-Step Implementation

---

### 1. Create a Knowledge Base

- Log in to AWS Console (us-east-2 region)
- Search for **Amazon Bedrock**
- In left sidebar, select **Knowledge Bases**
- Click **Create Knowledge Base**
- Choose **With vector store** option
- Set:
  - **Name:** `MyRAG-Chatbot`
  - **Description:** "Company documentation assistant"
  - **Service Role:** "Create new role"
- Take a screenshot of your setup page.
- Click **Next**

✅ Knowledge Base framework ready!

---

### 2. Connect S3 Documents

- Under **Data Source**, select **Amazon S3**
- Click **Browse S3** and select your bucket
- Set:
  - **Data source name:** `my-docs-source`
  - **Parsing strategy:** Default
  - **Chunking strategy:** Default (300 tokens)
- Click **Next**

#### 🛠 Configure Embeddings

- Select **Titan Text Embeddings v2**
- For Vector Store:
  - Choose **Quick create with OpenSearch Serverless**
- Click **Create Knowledge Base**

🧠 **Note:**  
This converts your documents into searchable "idea maps" the AI can navigate.

---

### 3. Sync Your Documents

- Go to **Knowledge Bases** > **Data Sources**
- Checkbox your `my-docs-source`
- Click **Sync**
- Wait for status to change from **In Progress** to **Available** (≈5 min)

🧠 **Note:**  
Syncing processes:
1. Text extraction from files
2. Chunking into paragraphs
3. Creating semantic search indexes

---

### 4. Enable AI Models

- Navigate to **Model Access** in Bedrock
- Click **Modify Model Access**
- Enable:
  - [x] Llama 3.1 8B Instruct
  - [x] Llama 3.3 70B Instruct
- Click **Submit** (instant approval)

#### ⚡ Model Choice
| Model           | Best For                  | Cost/1K Tokens |
|-----------------|---------------------------|----------------|
| Llama 3.1 8B    | Fast, simple queries      | $0.00022       |
| Llama 3.3 70B   | Complex reasoning         | $0.00072       |

---

### 5. Test Your Chatbot

- Go to **Knowledge Bases** > Select yours
- Click **Test Knowledge Base**
- Choose model: **Llama 3.3 70B Instruct**
- Try queries:
  - "Summarize our security policies"
  - "What projects did we complete last quarter?"
- Toggle **Generate Responses** to see raw vs polished answers


---

## 🧹 Clean Up (Recommended)

To avoid charges:
1. **Delete** Knowledge Base
2. **Empty & Delete** S3 bucket
3. **Remove** OpenSearch collection

---

# 🎉 Congratulations!

You've built an AI chatbot that answers questions using your company's knowledge!  
Next steps: Try adding more documents or customizing prompts. 🚀