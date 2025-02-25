# 🌍 Terraform Comprehensive Cheatsheet

## 🔹 Introduction
Terraform is an **Infrastructure as Code (IaC)** tool used for provisioning and managing cloud resources.

---

## 🔹 Installing Terraform
```sh
# Install Terraform on Ubuntu/Debian
sudo apt update && sudo apt install terraform -y

# Install Terraform on macOS
brew tap hashicorp/tap
brew install hashicorp/tap/terraform

# Verify installation
terraform version
```

---

## 🔹 Basic Commands
```sh
# Initialize Terraform in a directory
terraform init

# Format Terraform configuration files
terraform fmt

# Validate configuration files
terraform validate

# Plan the infrastructure changes
terraform plan

# Apply the infrastructure changes
terraform apply

# Destroy the infrastructure
terraform destroy
```

---

## 🔹 Writing a Terraform Configuration
### ✅ Create `main.tf`
```hcl
provider "aws" {
  region = "us-east-1"
}

resource "aws_instance" "example" {
  ami           = "ami-12345678"
  instance_type = "t2.micro"
}
```

---

## 🔹 Terraform State Management
```sh
# Show current state
terraform state list

# Show details of a specific resource
terraform state show aws_instance.example

# Remove a resource from the state file
terraform state rm aws_instance.example
```

---

## 🔹 Variables in Terraform
### ✅ Define Variables in `variables.tf`
```hcl
variable "instance_type" {
  description = "EC2 instance type"
  type        = string
  default     = "t2.micro"
}
```

### 📌 Use Variables in `main.tf`
```hcl
resource "aws_instance" "example" {
  ami           = "ami-12345678"
  instance_type = var.instance_type
}
```

### 📌 Pass Variables via CLI
```sh
terraform apply -var="instance_type=t3.micro"
```

---

## 🔹 Terraform Modules
### ✅ Create a Module
```plaintext
modules/
 ├── ec2/
 │   ├── main.tf
 │   ├── variables.tf
 │   ├── outputs.tf
```

### 📌 Use the Module in `main.tf`
```hcl
module "ec2" {
  source         = "./modules/ec2"
  instance_type  = "t3.micro"
}
```

---

## 🔹 Terraform Outputs
### ✅ Define Outputs in `outputs.tf`
```hcl
output "instance_ip" {
  value = aws_instance.example.public_ip
}
```

### 📌 Display Outputs
```sh
terraform output
```

---

## 🔹 Terraform Best Practices
- **Use remote state storage** (S3, Terraform Cloud) to avoid local state issues.
- **Use modules** for reusability and maintainability.
- **Version lock providers** to prevent unexpected updates.
- **Use workspaces** for managing different environments (dev, staging, production).
- **Automate Terraform with CI/CD** for better infrastructure management.

---