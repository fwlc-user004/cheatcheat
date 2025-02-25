# ☁️ Azure (VMs, Functions, Blob Storage) Comprehensive Cheatsheet

## 🔹 Introduction
Microsoft **Azure** is a cloud computing platform offering services like **Virtual Machines (VMs), Serverless Functions, and Blob Storage** for scalable and secure applications.

---

## 🔹 Azure Virtual Machines (VMs)
### ✅ VM Management
```sh
# List all VMs
az vm list --output table

# Create a VM
az vm create --name MyVM --resource-group MyResourceGroup --image UbuntuLTS --admin-username azureuser --generate-ssh-keys

# Start a VM
az vm start --name MyVM --resource-group MyResourceGroup

# Stop a VM
az vm stop --name MyVM --resource-group MyResourceGroup

# Delete a VM
az vm delete --name MyVM --resource-group MyResourceGroup --yes
```

### 📌 Connect to Azure VM via SSH
```sh
ssh azureuser@myvm.eastus.cloudapp.azure.com
```

---

## 🔹 Azure Functions (Serverless Computing)
### ✅ Create & Deploy an Azure Function
```sh
# Create a new Azure Function App
az functionapp create --name MyFunctionApp --resource-group MyResourceGroup --consumption-plan-location eastus --runtime python
```

### 📌 Deploy Code to Azure Function
```sh
# Zip and deploy function
func azure functionapp publish MyFunctionApp
```

### 📌 Invoke an Azure Function
```sh
# Invoke via HTTP request
curl https://myfunctionapp.azurewebsites.net/api/myfunction
```

### 📌 Monitor Azure Functions Logs
```sh
az functionapp log tail --name MyFunctionApp --resource-group MyResourceGroup
```

---

## 🔹 Azure Blob Storage
### ✅ Storage Account Management
```sh
# Create a storage account
az storage account create --name mystorageaccount --resource-group MyResourceGroup --location eastus --sku Standard_LRS
```

### 📌 Blob Container & File Management
```sh
# Create a Blob container
az storage container create --name mycontainer --account-name mystorageaccount

# Upload a file to Blob Storage
az storage blob upload --account-name mystorageaccount --container-name mycontainer --name myfile.txt --file myfile.txt

# List blobs in a container
az storage blob list --account-name mystorageaccount --container-name mycontainer --output table

# Download a blob
az storage blob download --account-name mystorageaccount --container-name mycontainer --name myfile.txt --file downloaded.txt
```

---

## 🔹 Azure Best Practices
- **Use Azure Resource Groups** to organize related resources.
- **Enable Auto-Scaling** for Azure Functions to handle high traffic.
- **Implement Role-Based Access Control (RBAC)** for secure VM management.
- **Use Azure Monitor & Application Insights** for logging and performance monitoring.
- **Configure Geo-Redundancy** for Blob Storage for disaster recovery.

---