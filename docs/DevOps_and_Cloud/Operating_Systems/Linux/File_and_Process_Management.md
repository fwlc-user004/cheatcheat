# 🏆 Linux File and Process Management Cheat Sheet

---

## 📌 1. File Management Commands

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

### 🔹 File Viewing and Editing
```sh
cat file.txt     # View file contents
less file.txt    # View large files page by page
head -n 10 file.txt   # Show first 10 lines
tail -n 10 file.txt   # Show last 10 lines
nano file.txt    # Open file in nano editor
vim file.txt     # Open file in Vim editor
```

---

## 📌 2. File Permissions and Ownership

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

## 📌 3. Searching for Files and Content

```sh
find / -name file.txt    # Find file named "file.txt"
grep "word" file.txt     # Search for "word" in file.txt
grep -r "text" /path     # Recursive search for text in directory
```

---

## 📌 4. Process Management

### 🔹 Viewing Processes
```sh
ps aux        # View running processes
top           # Display real-time system performance and processes
htop          # Interactive process manager (requires installation)
```

### 🔹 Managing Processes
```sh
kill PID      # Terminate process by PID
killall name  # Kill all processes with name
pkill -9 name # Force kill a process by name
```

### 🔹 Background and Foreground Processes
```sh
command &      # Run command in background
jobs           # Show background jobs
fg %1          # Bring job #1 to foreground
bg %1          # Resume job #1 in background
```

---

## 📌 5. Disk and Storage Management

```sh
df -h         # Show disk usage in human-readable format
du -sh folder # Show folder size
mount /dev/sdX /mnt  # Mount a drive
umount /mnt   # Unmount a drive
```

---

## 📌 6. File Archiving and Compression

```sh
tar -cvf archive.tar folder/  # Create a tar archive
tar -xvf archive.tar          # Extract tar archive
gzip file.txt                 # Compress file with gzip
gunzip file.txt.gz            # Decompress gzip file
```

---
