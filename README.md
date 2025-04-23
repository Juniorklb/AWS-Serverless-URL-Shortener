#  AWS Serverless URL Shortener

### ☁️ Built with Amazon Web Services (AWS)

![AWS](https://img.shields.io/badge/Built%20with-AWS-orange?style=flat&logo=amazonaws)
![Project Status](https://img.shields.io/badge/status-in--progress-yellow)

---

## 📌 Overview

This project is an **AWS serverless URL shortener** built on AWS. It allows users to generate short links that redirect to long URLs, like bit.ly or tinyurl  but using a fully scalable, pay-as-you-go architecture powered by AWS services.

---

## 🧱 Architecture Diagram

url-shortener/
├── lambda/
│   ├── create_short_url.py
│   └── redirect_handler.py
├── templates/
│   └── template.yaml
├── ui/
│   └── index.html (optional S3 hosted frontend)
├── README.md





## 🔧 Technologies Used

- **AWS Lambda** – Handles logic for creating and redirecting short links  
- **API Gateway** – Provides RESTful API access  
- **DynamoDB** – Stores original URLs and their short code mappings  
- **S3** *(optional)* – For hosting a simple frontend UI  
- **IAM** – Manages secure permissions  
- **Route 53** *(optional)* – Custom domain for short URLs  
- **CloudWatch** – Logs and monitoring  

---

## 🚀 Features

-  Generate short links for any URL  
-  Redirect users when short link is clicked  
-  Serverless and cost-efficient  
-  Scalable to handle high traffic  
-  (Optional) Simple HTML UI hosted on S3  

---

## 🛠️ Getting Started

### 🧰 Prerequisites

- AWS CLI configured
- Node.js / Python (depending on your Lambda language)
- SAM / Serverless Framework / Terraform (deployment method)

### 📦 Deployment

1. **Clone the repository**
   ```bash
   git clone https://github.com/Juniorklb/aws-serverless-url-shortener.git
   cd aws-serverless-url-shortener


