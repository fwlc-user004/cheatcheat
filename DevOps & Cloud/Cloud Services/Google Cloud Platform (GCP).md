# ☁️ Google Cloud Platform (GCP) Comprehensive Cheatsheet

## 🔹 Introduction
Google Cloud Platform (**GCP**) provides scalable cloud computing services. This cheatsheet covers **Compute Engine (VMs), Cloud Functions (Serverless), and Cloud Storage**.

---

## 🔹 Compute Engine (Virtual Machines)
### ✅ VM Management
```sh
# List all VMs
gcloud compute instances list

# Create a VM instance
gcloud compute instances create my-vm --zone=us-central1-a --machine-type=e2-medium --image-family=debian-11 --image-project=debian-cloud

# Start a VM
gcloud compute instances start my-vm --zone=us-central1-a

# Stop a VM
gcloud compute instances stop my-vm --zone=us-central1-a

# Delete a VM
gcloud compute instances delete my-vm --zone=us-central1-a --quiet
```

### 📌 Connect to a VM via SSH
```sh
gcloud compute ssh my-vm --zone=us-central1-a
```

---

## 🔹 Cloud Functions (Serverless Computing)
### ✅ Create & Deploy a Cloud Function
```sh
# Create a new Cloud Function
gcloud functions deploy my-function --runtime python39 --trigger-http --allow-unauthenticated --region=us-central1
```

### 📌 Invoke a Cloud Function
```sh
# Call the function via HTTP request
curl https://us-central1-my-project.cloudfunctions.net/my-function
```

### 📌 View Logs
```sh
gcloud functions logs read my-function
```

---

## 🔹 Cloud Storage (Object Storage)
### ✅ Storage Bucket Management
```sh
# List all storage buckets
gcloud storage buckets list

# Create a storage bucket
gcloud storage buckets create my-bucket --location=us-central1
```

### 📌 Upload & Download Files
```sh
# Upload a file to a bucket
gcloud storage cp myfile.txt gs://my-bucket/

# Download a file from a bucket
gcloud storage cp gs://my-bucket/myfile.txt ./
```

### 📌 Make a File Public
```sh
gcloud storage objects add-iam-policy-binding gs://my-bucket/myfile.txt --role=roles/storage.objectViewer --member=allUsers
```

---

## 🔹 Networking & Security
### ✅ Firewall Rules
```sh
# List firewall rules
gcloud compute firewall-rules list

# Create a firewall rule to allow HTTP
gcloud compute firewall-rules create allow-http --allow=tcp:80 --target-tags=http-server
```

---

## 🔹 GCP Best Practices
- **Use IAM Roles** to restrict permissions.
- **Enable Auto-Scaling** for Compute Engine instances.
- **Use Cloud Logging & Monitoring** for debugging.
- **Set up Load Balancing** for high-availability applications.
- **Use Cloud Storage Lifecycle Policies** to manage data retention.

---