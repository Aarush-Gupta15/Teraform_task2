# Task 2 – Terraform AWS Infrastructure

This project provisions AWS infrastructure using Terraform. It includes:
- A custom VPC
- Public and private subnets
- Internet Gateway
- Route Tables
- EC2 Instance

The project is configured to use **remote state storage in S3** with optional **DynamoDB state locking**.

---

## 🧾 Project Structure
task2/ ├── main.tf # Root Terraform config with backend ├── variables.tf # Input variables ├── terraform.tfvars # Variable values (not pushed to Git) ├── outputs.tf # Output values (e.g., public IP) ├── modules/ # Reusable modules (vpc, ec2, etc.)


---

## 🔧 Prerequisites

- AWS CLI configured with your credentials (`aws configure`)
- Terraform installed (v1.0+)
- An S3 bucket (for remote backend)
- Optional: DynamoDB table for state locking (`LockID` as partition key)

---

## 🚀 How to Use

### 1. Clone this repository

```bash
git clone https://github.com/Aarush-Gupta15/Teraform_Tasks.git
cd Teraform_Tasks/task2
```

2. Initialize Terraform
bash
Copy
Edit
terraform init
This will configure the remote backend with your S3 bucket and (optionally) DynamoDB for locking.

3. Preview the Infrastructure
bash
Copy
Edit
terraform plan

4. Apply the Configuration
bash
Copy
Edit
terraform apply

📦 Remote Backend
The Terraform state file is stored securely in an S3 bucket:

terraform {
  backend "s3" {
    bucket         = "your-bucket-name"
    key            = "Task2/terraform.tfstate"
    region         = "us-east-1"
    encrypt        = true
    dynamodb_table = "terraform-lock-table"  # Optional for state locking
  }
}

