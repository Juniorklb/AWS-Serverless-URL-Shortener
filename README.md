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

  ## 1 Create table with DynamodDB

 1.  Go to DynamoDB in AWS Console.

 2.  Click “Create table.”

 3.  Enter:

    Table name: UrlShortener

    Partition key: shortId (String)

![image alt](https://github.com/Juniorklb/AWS-Serverless-URL-Shortener/blob/1e8ef7ea1b3abe3a359abc14d028cc503eef5fb0/Images/Dynamobd.PNG)
   
4. Leave the rest as default and click Create table.
   
![image alt](https://github.com/Juniorklb/AWS-Serverless-URL-Shortener/blob/94e246deabe545de034cdf84a2db44c573bf74fa/Images/Dynamobd%202.PNG)

   ## 2 create Lambda Function – Shorten URL

   1. Go to AWS Lambda
      
      Visit the AWS Console

      Navigate to Lambda service

      Click “Create function.”

   2. Choose settings
      
      Function name: shorten_url

      Runtime: Python 3.9, 3.10
      
   ![image_alt](https://github.com/Juniorklb/AWS-Serverless-URL-Shortener/blob/698309afbc95e6dec142975d620055734f8d5442/Images/Lambda%201.PNG)
   
      Execution role:

      Choose “Create a new role with basic Lambda permissions.”   

  ![image_alt](https://github.com/Juniorklb/AWS-Serverless-URL-Shortener/blob/fc7b27baffe8cae13b97d777064e639c8ce5bd32/Images/Lambda%202.PNG)
  
  ## 3 Add Environment Variable
      
     Scroll to "Environment variables."

  Add:
    Key: TABLE_NAME
    Value: UrlShortener

  Click Save

  ## 4 Replace the default Lambda code

In the code editor, paste this full code:

    import json
    import boto3
    import os
    import string
    import random

    dynamodb = boto3.resource('dynamodb')
    table = dynamodb.Table(os.environ['TABLE_NAME'])

    def generate_short_id(length=6):
    return ''.join(random.choices(string.ascii_letters + string.digits, k=length))

    def lambda_handler(event, context):
    body = json.loads(event['body'])
    long_url = body.get('longUrl')

    if not long_url:
        return {
            'statusCode': 400,
            'body': json.dumps({'message': 'Missing longUrl'})
        }

    short_id = generate_short_id()
    
    table.put_item(
        Item={
            'shortId': short_id,
            'longUrl': long_url
        }
    )

    short_url = f"https://yourdomain.com/{short_id}"  # Replace with actual domain or API Gateway URL

    return {
        'statusCode': 200,
        'body': json.dumps({'shortUrl': short_url})
    }
Click Deploy

## 5 Update the IAM Role to Allow DynamoDB Access

In the Lambda page, go to Configuration → Permissions

Click the Role name under "Execution Role"

In the IAM console:

Click Add permissions → Create inline policy

Choose Service: DynamoDB

Actions: PutItem

Resources: Choose your table: arn:aws:dynamodb:...:table/UrlShortener

Click Review Policy, give it a name like DynamoDBPutItemPolicy, then Create policy

</b>
<h2>👥 Connect with me:</h2>

<p align="left">
  <a href="https://www.linkedin.com/in/junior-kalomba-10002a18a/" target="_blank">
    <img src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/linked-in-alt.svg" alt="junior-kalomba-10002a18a" height="30" width="40"/>  
    
  </a>
  <a href="mailto:jrkalomba@gmail.com" target="_blank">
  <img  src="https://upload.wikimedia.org/wikipedia/commons/4/4e/Mail_%28iOS%29.svg" alt="Email" height="30" width="40"/>
</a>
</p>


[linkedin]: https://linkedin.com/in/Juniorkalomba

**🔗 Feel free to contribute or suggest improvements!**


   
