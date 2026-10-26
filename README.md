# AWS Application Load Balancer using Terraform

## 📌 Project Overview

This project demonstrates the provisioning of AWS infrastructure using **Terraform (Infrastructure as Code)**. It automates the creation and configuration of networking, compute templates, target groups, DNS, SSL/TLS certificates, and an Application Load Balancer.

The goal is to understand how AWS resources work together to route incoming application traffic through a load balancer.

## 🏗️ Architecture

The project follows this deployment sequence:

1. **VPC** – Networking foundation, subnets, and security groups.
2. **Launch Template (LT)** – EC2 instance configuration.
3. **Target Group (TG)** – Backend target registration and health checks.
4. **DNS** – Route 53 DNS configuration.
5. **ACM** – SSL/TLS certificate provisioning.
6. **Application Load Balancer (ALB)** – Listener configuration and traffic routing.

### Architecture Flow

```text
                    Users
                      |
                      v
               Route 53 DNS
                      |
                      v
              Application Load
                 Balancer
                      |
               Listener Rules
                      |
                      v
                Target Group
                      |
               EC2 Instances
```

*Note: The diagram is a logical overview. Actual routing, HTTPS configuration, subnet placement, and target registration depend on the deployed Terraform configuration.*

## 🛠️ Technologies Used

- Amazon Web Services (AWS)
- Terraform
- Amazon VPC
- Amazon EC2 Launch Templates
- Application Load Balancer (ALB)
- Elastic Load Balancing Target Groups
- Amazon Route 53
- AWS Certificate Manager (ACM)
- Git and GitHub

## 📂 Project Structure

```text
aws-application-load-balancer-terraform/
├── environments/
│   ├── network/
│   │   └── vpc/
│   │       └── dev/
│   └── Compute/
│       ├── lt/
│       ├── tg/
│       ├── dns/
│       ├── acm-alb/
│       └── alb/
├── modules/
├── .gitignore
└── README.md
```

*Adjust the directory tree to match the actual repository structure.*

## ⚙️ Deployment Workflow

### Prerequisites

- An AWS account
- AWS CLI configured with appropriate permissions
- Terraform installed
- Git installed
- A domain and DNS configuration if using a custom domain and HTTPS

### Step 1: Configure AWS credentials

Configure credentials securely using an AWS CLI profile or an appropriate IAM role.

```bash
aws configure
```

Verify the active identity:

```bash
aws sts get-caller-identity
```

### Step 2: Initialize Terraform

Navigate to the relevant Terraform environment directory.

```bash
terraform init
```

### Step 3: Review the execution plan

```bash
terraform plan
```

### Step 4: Deploy infrastructure

```bash
terraform apply
```

Review the plan and confirm the deployment when prompted.

### Step 5: Verify the deployment

Check the Terraform outputs:

```bash
terraform output
```

Verify the ALB state, listener configuration, target health, and DNS response through the AWS Console or AWS CLI.

## 🔐 Security Best Practices

- Follow the principle of least privilege for IAM permissions.
- Never commit AWS access keys, private keys, or sensitive `.tfvars` files.
- Keep Terraform state files out of public repositories.
- Restrict security group access to only required ports and trusted sources.
- Use HTTPS with a valid ACM certificate when configured.
- Store Terraform state remotely with appropriate access controls and encryption when needed.

## 🧹 Cleanup

To avoid unnecessary AWS charges, review the infrastructure dependencies and destroy resources when they are no longer required.

```bash
terraform plan -destroy
terraform destroy
```

Run destroy commands from the appropriate Terraform environment directories and ensure dependent resources are handled in the correct order.

## 🎯 Key Learnings

- Infrastructure provisioning using Terraform
- AWS VPC and networking fundamentals
- EC2 Launch Template configuration
- Load balancing and target group health checks
- DNS management and SSL/TLS certificate integration
- Terraform resource dependencies and deployment workflow

## 👩‍💻 Author

**Sakshi Repale**

Aspiring AWS & DevOps Engineer

GitHub: [repalesakshi-debug](https://github.com/repalesakshi-debug)

---

⭐ If you find this project useful, feel free to explore the repository and share feedback.
