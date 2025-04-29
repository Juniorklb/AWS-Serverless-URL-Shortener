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
    │    └── template.yaml
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
## Project Structure

- Set up DynamoDB table
- Create Lambda functions
  
       shorten_url: Generates a short URL and stores mapping
       redirect_url: Redirects short URL to the original URL

- Connect Lambda to API Gateway
- Optional Frontend (HTML + JS on S3)

  ## Step 1 Create table with DynamodDB

 1.  Go to DynamoDB in AWS Console.

 2.  Click “Create table.”

 3.  Enter:

    Table name: UrlShortener

    Partition key: shortId (String)

    
   
4. Leave the rest as default and click Create table.

   ## Step 2 create Lambda Function – Shorten URL

   1. Go to AWS Lambda
      
      Visit the AWS Console

      Navigate to Lambda service

      Click “Create function.”

   2. Choose settings
      
      Function name: shorten_url

      Runtime: Python 3.9, 3.10

      Execution role:

Choose “Create a new role with basic Lambda permissions.”   


  3. Add Environment Variable
      
     Scroll to "Environment variables."

 Add:

    Key: TABLE_NAME

    Value: UrlShortener

 Click Save

   
