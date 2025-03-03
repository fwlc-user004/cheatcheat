# 🏆 Windows Command Prompt Cheat Sheet

---

## 📌 1. Introduction to Windows Command Prompt

The **Windows Command Prompt (CMD)** is a command-line interpreter for executing system commands, managing files, and configuring Windows settings.

### 🔹 Opening Command Prompt
- **Shortcut**: Press `Win + R`, type **cmd**, and press `Enter`
- **Search Method**: Click **Start**, type **Command Prompt**, and open it.

---

## 📌 2. Basic Navigation Commands

```cmd
cd C:\Users        # Change directory
cd ..              # Move up one level
cd /d D:\Folder    # Change drive and directory
dir                # List files and directories
```

---

## 📌 3. File and Directory Management

```cmd
mkdir NewFolder    # Create a new directory
rmdir FolderName   # Remove an empty directory
rmdir /s Folder    # Remove directory and all contents
del file.txt       # Delete a file
copy file1 file2   # Copy a file
move file1 file2   # Move/rename a file
```

---

## 📌 4. File Viewing and Editing

```cmd
type file.txt      # Display file contents
more file.txt      # View file contents page by page
notepad file.txt   # Open file in Notepad
```

---

## 📌 5. System Information Commands

```cmd
systeminfo         # Show detailed system information
hostname           # Display computer name
ver                # Show Windows version
wmic os get name   # Get OS details
```

---

## 📌 6. Process and Task Management

```cmd
tasklist           # Display running processes
taskkill /IM name  # Kill process by name
taskkill /PID 1234 # Kill process by process ID
```

---

## 📌 7. Network Commands

```cmd
ipconfig /all      # Display network information
ping google.com    # Test network connectivity
tracert google.com # Trace network route to a host
netstat -an        # Show active network connections
```

---

## 📌 8. User Management

```cmd
whoami             # Show current user
net user           # List all user accounts
net user username  # Display details of a user
```

---

## 📌 9. Disk and File System Commands

```cmd
chkdsk C:          # Check disk for errors
diskpart           # Open disk partition tool
```

---

## 📌 10. Windows Utility Commands

```cmd
shutdown /s /t 0   # Shutdown the computer
shutdown /r /t 0   # Restart the computer
cls                # Clear the screen
exit               # Close Command Prompt
```

---
