# ☁️ Cloud Music Platform – AWS CDK Backend

This repository contains the **Infrastructure as Code (IaC)** and **Lambda backend services** for the **Cloud Music Streaming Platform**.

The backend is built using the **AWS Cloud Development Kit (CDK)** in **Python**, following **cloud-native architecture** principles.  
It provisions all required AWS services and deploys Lambda functions, APIs, and other resources automatically.

---

## 🎯 Project Overview

The system is a **cloud-native music streaming web application** that enables users to:
- Store, share, and listen to music content through the cloud.
- Access personalized recommendations and subscriptions.
- Manage offline playback and notifications.

### 👥 User Roles
| Role | Description |
|------|--------------|
| **Guest** | Can register and log in. |
| **Regular User** | Can browse, filter, and rate songs, subscribe to artists or genres, receive notifications, and manage offline playback. |
| **Administrator** | Can upload, edit, and delete songs, albums, and artist data. |

---

## 🏗️ Architecture Overview

The system follows a **cloud-native, event-driven architecture** using AWS managed services:

| Component | AWS Service | Purpose |
|------------|-------------|----------|
| **Authentication** | Amazon Cognito | Manages user registration, login, and token validation. |
| **Storage** | Amazon S3 | Stores audio files, album covers, and other media content. |
| **Metadata** | Amazon DynamoDB | Stores metadata about songs, artists, genres, and ratings. |
| **APIs** | Amazon API Gateway | Entry point for client requests, exposing REST endpoints. |
| **Business Logic** | AWS Lambda | Implements core logic for content management and subscriptions. |
| **Notifications** | Amazon SNS / WebSocket | Sends real-time or email notifications to subscribed users. |
| **Queues (Async)** | Amazon SQS | Handles asynchronous communication and decoupling between services. |
| **Transcription (Optional)** | Amazon Transcribe | Generates lyrics automatically for uploaded audio files. |
| **Frontend Hosting** | S3 + CloudFront | Hosts the React/Angular web client (deployed separately). |

---

## ⚙️ Development Setup

### 1️⃣ Create and activate virtual environment
```bash
python -m venv .venv
source .venv/bin/activate   # Mac/Linux
.venv\Scripts\activate.bat  # Windows
```

### 2️⃣ Install dependencies
```bash
pip install -r requirements.txt
```

### 3️⃣ Synthesize CloudFormation templates
```bash
cdk synth
```

### 4️⃣ Deploy to AWS
```bash
cdk deploy
```

### 5️⃣ Useful CDK Commands
| Command | Description |
|----------|-------------|
| `cdk ls` | List all stacks |
| `cdk synth` | Generate CloudFormation template |
| `cdk deploy` | Deploy the stack to AWS |
| `cdk diff` | Compare current and deployed state |
| `cdk destroy` | Remove all deployed resources |

---

## 🧠 Key Features (from Specification)

✅ **User Registration and Login (Cognito)**  
✅ **Artist and Song Management (S3 + DynamoDB)**  
✅ **Filtering / Discover Page (Genre-based)**  
✅ **Subscriptions with Notifications (SNS / SQS)**  
✅ **Offline Playback (S3 Presigned URLs)**  
✅ **Rating and Personalized Feed (Lambda logic + DynamoDB)**  
✅ **Infrastructure as Code (AWS CDK – imperative)**  
✅ **Event-driven communication**  

---

## 🚀 Deployment Notes
- Media upload uses **S3 presigned URLs** to bypass the 10 MB API Gateway limit.  
- Notification system uses **SNS** for user alerts.  
- Follow **event-driven principles**: use SQS queues where asynchronous flow makes sense.  

---

## 📘 References

- [AWS Lambda Packaging for Python](https://docs.aws.amazon.com/lambda/latest/dg/python-package.html)  
- [AWS CDK Documentation](https://docs.aws.amazon.com/cdk/latest/guide/home.html)  
- [AWS Cognito User Pools vs Identity Pools](https://tutorialsdojo.com/amazon-cognito-user-pools-vs-identity-pools/)  
- [Serverless Python Requirements Plugin](https://www.serverless.com/plugins/serverless-python-requirements)  

---

## 👩‍💻 Team
**Role:** Cloud Developer – Team Member  
**Technologies:** AWS CDK, Lambda, API Gateway, DynamoDB, S3, Cognito, SNS, SQS, CloudFront  
