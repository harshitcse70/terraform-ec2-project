# Terraform EC2 Instance Deployment (Basic Setup)

##  Project Overview

This project demonstrates a **basic Infrastructure as Code (IaC)** implementation using Terraform to provision an **AWS EC2 instance**.

It focuses mainly on:

* Writing Terraform configuration (`main.tf`)
* Launching an EC2 instance
* Creating and attaching a security group
* Understanding Terraform workflow (init → plan → apply → destroy)

---

##  Objectives

* Learn Terraform fundamentals
* Provision AWS resources using code
* Understand EC2 setup via Terraform
* Practice basic DevOps workflow

---

## Project Structure

```id="p5h6jl"
terraform-ec2-project/
│
├── main.tf                # Main Terraform configuration
├── .gitignore            # Ignore sensitive files
├── .terraform.lock.hcl   # Provider dependency lock file
```

---

##  Technologies Used

* **Terraform**
* **AWS EC2**
* **AWS Security Groups**

---

##  Infrastructure Created

### 🔹 1. EC2 Instance

* Instance type: `t3.micro` (Free Tier eligible)
* AMI: Amazon Linux (via data source or static AMI)
* Key pair: Used for SSH access

---

###  2. Security Group

Allows:

*  SSH access (port 22) from anywhere
*  All outbound traffic

---

##  Terraform Workflow

###  Initialize Terraform

```bash
terraform init
```

---

###  Validate Configuration

```bash
terraform validate
```

---

###  Plan Execution

```bash
terraform plan
```

---

###  Apply Changes

```bash
terraform apply
```

---

###  Destroy Resources (Optional)

```bash
terraform destroy
```

---

##  Security Considerations

* SSH access is open to `0.0.0.0/0` (not recommended for production)
* Key pair is required for secure login
* `.pem` files are excluded using `.gitignore`

---

##  Limitations of This Approach

This project uses **local state**, which has several drawbacks:

- State file stored locally
- Not suitable for team collaboration
- Risk of state loss
- No locking mechanism
- Difficult to scale

---

##  Improvement: Remote State (Advanced Version)

To overcome these limitations, the project can be upgraded using:

* **Amazon S3** → Store Terraform state remotely
* **DynamoDB** → Enable state locking

###  Benefits:

* Centralized state management
* Team collaboration support
* Prevents concurrent changes
* Versioning and recovery

Note: A more advanced version of this project implements this using a **bootstrap + remote backend architecture**:  
 [terraform-aws-ec2-remote-backend](https://github.com/harshitcse70/terraform-aws-ec2-remote-backend)

---


