# ☁️ AWS (S3, EC2, Lambda, RDS) Comprehensive Cheatsheet

## 🔹 Introduction
Amazon Web Services (**AWS**) provides scalable cloud computing solutions. This cheatsheet covers **S3 (Storage), EC2 (Compute), Lambda (Serverless), and RDS (Databases)**.

---

## 🔹 Amazon S3 (Simple Storage Service)
### ✅ Bucket Management
```sh
# List all buckets
aws s3 ls

# Create a new bucket
aws s3 mb s3://my-bucket-name

# Delete a bucket
aws s3 rb s3://my-bucket-name --force
```

### 📌 Upload & Download Files
```sh
# Upload a file to S3
aws s3 cp myfile.txt s3://my-bucket-name/

# Download a file from S3
aws s3 cp s3://my-bucket-name/myfile.txt ./
```

### 📌 Enable Public Access
```sh
aws s3api put-bucket-acl --bucket my-bucket-name --acl public-read
```

---

## 🔹 Amazon EC2 (Elastic Compute Cloud)
### ✅ Instance Management
```sh
# List all instances
aws ec2 describe-instances

# Start an instance
aws ec2 start-instances --instance-ids i-1234567890abcdef

# Stop an instance
aws ec2 stop-instances --instance-ids i-1234567890abcdef

# Terminate an instance
aws ec2 terminate-instances --instance-ids i-1234567890abcdef
```

### 📌 SSH into an EC2 Instance
```sh
ssh -i my-key.pem ec2-user@your-ec2-ip
```

### 📌 Security Group Management
```sh
# Open port 80 (HTTP)
aws ec2 authorize-security-group-ingress --group-id sg-12345 --protocol tcp --port 80 --cidr 0.0.0.0/0
```

---

## 🔹 AWS Lambda (Serverless)
### ✅ Create & Deploy a Lambda Function
```sh
# Create a Lambda function
aws lambda create-function --function-name myLambda --runtime python3.8 --role arn:aws:iam::123456789012:role/execution_role --handler lambda_function.lambda_handler --zip-file fileb://function.zip
```

### 📌 Invoke a Lambda Function
```sh
aws lambda invoke --function-name myLambda output.txt
```

### 📌 Delete a Lambda Function
```sh
aws lambda delete-function --function-name myLambda
```

---

## 🔹 Amazon RDS (Relational Database Service)
### ✅ Database Management
```sh
# List all RDS instances
aws rds describe-db-instances

# Create an RDS instance
aws rds create-db-instance --db-instance-identifier mydb --db-instance-class db.t2.micro --engine mysql --master-username admin --master-user-password password
```

### 📌 Connect to RDS Instance (MySQL Example)
```sh
mysql -h mydb.cluster-xyz.rds.amazonaws.com -u admin -p
```

### 📌 Delete an RDS Instance
```sh
aws rds delete-db-instance --db-instance-identifier mydb --skip-final-snapshot
```

---

## 🔹 AWS Best Practices
- **Use IAM Roles** instead of storing credentials in code.
- **Enable S3 Versioning** for backup and recovery.
- **Use Auto Scaling Groups** for EC2 to manage traffic spikes.
- **Enable Multi-AZ for RDS** for high availability.
- **Monitor with AWS CloudWatch** for logs and performance metrics.

---