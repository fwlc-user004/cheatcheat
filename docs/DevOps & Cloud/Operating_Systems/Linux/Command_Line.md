# 🏆 Ultimate Linux Command Line Cheat Sheet

---

## 📌 1. Introduction to the Linux Command Line

The **Linux command line** is a powerful tool for interacting with the operating system. It allows users to **navigate directories, manage files, execute programs, and control system processes**.

To open a terminal:
- **Ubuntu/Debian**: Press `Ctrl + Alt + T`
- **CentOS/RHEL**: Search for “Terminal” in the application menu

---

## 📌 2. File and Directory Commands

### 🔹 Navigating Directories
```sh
pwd         # Print current working directory
ls          # List files in directory
ls -l       # List with details (permissions, size, modification date)
ls -a       # Show hidden files
cd /path    # Change directory
cd ..       # Move up one level
cd ~        # Go to home directory
```

### 🔹 File Operations
```sh
touch file.txt      # Create an empty file
cp file1 file2      # Copy file1 to file2
mv file1 file2      # Rename/move file1 to file2
rm file.txt         # Delete file
rm -r directory/    # Remove directory and its contents
```

### 🔹 Directory Operations
```sh
mkdir new_folder    # Create a directory
rmdir empty_folder  # Remove empty directory
rm -rf folder/      # Delete directory and all contents
```

---

## 📌 3. File Viewing and Editing

```sh
cat file.txt     # View file contents
less file.txt    # View large files page by page
head -n 10 file.txt   # Show first 10 lines
tail -n 10 file.txt   # Show last 10 lines
nano file.txt    # Open file in nano editor
vim file.txt     # Open file in Vim editor
```

---

## 📌 4. File Permissions

### 🔹 Changing File Permissions
```sh
chmod 755 file.txt     # Give owner full access, others read+execute
chmod u+x script.sh    # Make script executable
```

### 🔹 Changing File Ownership
```sh
chown user file.txt    # Change file owner
chown user:group file.txt  # Change owner and group
```

---

## 📌 5. Searching for Files and Text

```sh
find / -name file.txt    # Find file named "file.txt"
grep "word" file.txt     # Search for "word" in file.txt
grep -r "text" /path     # Recursive search for text in directory
```

---

## 📌 6. Process Management

```sh
ps aux        # View running processes
top           # Display real-time system performance and processes
kill PID      # Terminate process by PID
killall name  # Kill all processes with name
htop          # Interactive process manager (requires installation)
```

---

## 📌 7. Disk and Storage Management

```sh
df -h         # Show disk usage in human-readable format
du -sh folder # Show folder size
mount /dev/sdX /mnt  # Mount a drive
umount /mnt   # Unmount a drive
```

---

## 📌 8. Networking Commands

```sh
ip a         # Show network interfaces and IP addresses
ping 8.8.8.8 # Test network connectivity
curl -I website.com  # Get HTTP headers
wget file_url # Download file from URL
```

---

## 📌 9. User Management

```sh
whoami         # Show current user
id             # Show user ID and group info
adduser name   # Add new user
deluser name   # Remove user
passwd         # Change password
```

---

## 📌 10. Package Management

### 🔹 Debian-based (Ubuntu, Debian)
```sh
apt update         # Update package list
apt upgrade        # Upgrade installed packages
apt install pkg    # Install a package
apt remove pkg     # Remove a package
```

### 🔹 Red Hat-based (CentOS, RHEL)
```sh
yum update         # Update all packages
yum install pkg    # Install a package
yum remove pkg     # Remove a package
```

---

## 📌 11. System Monitoring

```sh
uptime      # Show system uptime
free -m     # Show memory usage
vmstat      # Display system performance stats
```

---

## 📌 12. Archiving and Compression

```sh
tar -cvf archive.tar folder/  # Create a tar archive
tar -xvf archive.tar          # Extract tar archive
gzip file.txt                 # Compress file with gzip
gunzip file.txt.gz            # Decompress gzip file
```

---

## 📌 13. SSH and Remote Access

```sh
ssh user@server     # Connect to a remote server
scp file user@server:/path  # Secure copy file to server
rsync -avz source destination  # Sync files between systems
```

---
