# CloudOps Warden: Serverless Auto-Governance Pipeline

A production-ready, event-driven FinOps tool engineered using AWS CloudFormation (Infrastructure as Code) and Python (Boto3). This solution autonomously enforces corporate financial governance by identifying and reporting idle, money-wasting resources across an AWS infrastructure.

## 🚀 The Problem It Solves (FinOps Strategy)
In enterprise cloud environments, cost-effectiveness is a mandatory requirement. Orphaned resources—such as unattached Elastic Block Store (EBS) volumes and unassociated Elastic IP addresses—silently accumulate heavy costs. CloudOps Warden completely automates the tracking of these resources, removing human error and reducing operational overhead to exactly $0.00 using a 100% serverless blueprint.

## 🏗️ Architecture Overview
The pipeline utilizes a fully decoupled, event-driven architecture:
* **AWS EventBridge (Cron Trigger):** Triggers the governance engine automatically on a daily schedule.
* **AWS Lambda (Execution Core):** Runs a lightweight Python 3.9 script using the AWS Boto3 SDK to audit the infrastructure.
* **AWS IAM (Least Privilege Security):** Uses a dedicated execution role strictly scoped down to read-only resource access and specific writing access.
* **Amazon S3 (Dashboard Hosting):** Dynamically updates and hosts a static HTML reporting dashboard.
* **Amazon SNS (Alerting Engine):** Instantly publishes a Pub/Sub email alert to the Cloud Operations team upon successful audit completion.

## 🛠️ Deployment Instructions

1. **Clone the repository:**
   git clone https://github.com/Harsh-Upadhyay2004/cloudops-warden.git
   cd cloudops-warden

2. **Deploy via AWS CLI:**
   aws cloudformation deploy \
     --template-file warden.yaml \
     --stack-name CloudOpsWarden \
     --parameter-overrides AlertEmail=h.upadhyay13082004@gmail.com \
     --capabilities CAPABILITY_IAM \
     --region ap-south-1

## 📊 Dashboard Preview
Once running, the Lambda engine outputs a clean, responsive HTML report directly to your public S3 website endpoint, giving teams instantaneous visibility into infrastructure waste without needing console access.
