# Cloud Security Assessment (AWS/Azure)
### *Cloud Pentesting | IAM Misconfigurations | Serverless Security*

## Overview
This project focuses on **cloud security testing** by deploying a **vulnerable AWS/Azure environment** to simulate **S3 bucket misconfigurations, privilege escalation, and API abuse**. The goal is to **identify security gaps, demonstrate exploitability, and provide remediation steps**.

## Features
- 🛠 **Misconfigured S3 Bucket** – Public access enabled, exposing sensitive data.  
- 🔑 **Privilege Escalation** – Exploiting weak IAM permissions for unauthorized access.  
- 📡 **API Exploitation** – Intercepting and modifying API requests to escalate privileges.  
- 🏗 **Serverless Security** – Attacking vulnerable AWS Lambda/Azure Functions.  

## Technologies Used
- **AWS Services** – S3, IAM, Lambda, API Gateway  
- **Azure Services** – Blob Storage, Managed Identities, Functions, Key Vault  
- **Tools** – AWS CLI, Pacu (AWS exploitation framework), ScoutSuite (cloud security auditing), Burp Suite  

## Repository Structure
```
/
│── infrastructure/  # Terraform scripts for deploying vulnerable AWS/Azure setup
│   ├── aws/         # AWS-specific infrastructure deployment
│   │   ├── main.tf  # Terraform script for AWS
│   │   ├── variables.tf
│   │   ├── outputs.tf
│   ├── azure/       # Azure-specific infrastructure deployment
│   │   ├── main.tf  # Terraform script for Azure
│   │   ├── variables.tf
│   │   ├── outputs.tf
│── exploitation/    # Security testing scripts
│   ├── s3_exploit.py
│   ├── iam_privesc.py
│   ├── api_abuse.py
│── mitigation/      # Security best practices and fixes
│   ├── aws_mitigations.md
│   ├── azure_mitigations.md
│── reports/         # Sample security assessment reports
│── README.md        # Project documentation
│── requirements.txt # Dependencies (if needed)
```

## Setup and Deployment
### Prerequisites
- AWS or Azure account with IAM access  
- AWS CLI / Azure CLI installed  
- Terraform (optional for automated deployment)  

### Deployment Steps
#### **AWS Setup**
1. Initialize Terraform and deploy resources:
   ```sh
   cd infrastructure/aws
   terraform init
   terraform apply -auto-approve
   ```
2. Verify deployed S3 bucket and IAM role permissions.

#### **Azure Setup**
1. Initialize Terraform and deploy resources:
   ```sh
   cd infrastructure/azure
   terraform init
   terraform apply -auto-approve
   ```
2. Validate deployed storage account and role assignments.

## Exploitation and Attack Scenarios
### 🔥 **S3 Bucket Takeover**
- Use `aws s3 ls s3://vulnerable-bucket/` to verify public access.  
- Exploit public bucket to retrieve **sensitive files**.  

### 🔑 **Privilege Escalation via IAM Policies**
- Use **Pacu (AWS exploitation framework)** to enumerate IAM policies:  
  ```sh
  pacu exploit iam__privesc_scan
  ```
- Exploit a misconfigured role to **escalate privileges**.

### ⚡ **Serverless Exploitation**
- Deploy a vulnerable AWS Lambda function.  
- Modify API Gateway requests to **inject malicious payloads**.  

## Mitigation Strategies
- Restrict **S3 bucket access** using proper ACLs and bucket policies.  
- Follow **Principle of Least Privilege (PoLP)** for IAM permissions.  
- Encrypt **sensitive data at rest and in transit**.  
- Implement **logging and monitoring** for suspicious activities.  

## Reporting and Documentation
- Generate a **detailed penetration testing report** on the findings.  
- Use **ScoutSuite** for cloud security auditing:  
  ```sh
  scout aws --services s3,iam,lambda
  ```
- Provide remediation steps based on industry best practices.

## Contributing
Pull requests are welcome! If you have suggestions for additional attack vectors, feel free to contribute.

## Disclaimer
**This project is for educational purposes only. Unauthorized testing on third-party cloud environments is illegal.*
