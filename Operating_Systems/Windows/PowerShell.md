# PowerShell Cheat Sheet

## 🔹 Basic Cmdlets
| Cmdlet | Description |
|--------|-------------|
| `Get-Help` | Displays help information about commands |
| `Get-Command` | Lists all available PowerShell commands |
| `Get-Process` | Shows currently running processes |
| `Stop-Process -Name <name>` | Stops a process by name |
| `Get-Service` | Lists all services |
| `Start-Service <name>` | Starts a service |
| `Stop-Service <name>` | Stops a service |
| `Restart-Service <name>` | Restarts a service |
| `Get-EventLog -LogName System` | Displays system event logs |
| `Clear-Host` | Clears the console screen |

## 🔹 File System Commands
| Cmdlet | Description |
|--------|-------------|
| `Get-Location` | Shows the current directory |
| `Set-Location <path>` | Changes the current directory |
| `Get-ChildItem <path>` | Lists files and directories (similar to `ls`) |
| `New-Item <file>` | Creates a new file or directory |
| `Remove-Item <file>` | Deletes a file or directory |
| `Copy-Item <src> <dest>` | Copies a file or directory |
| `Move-Item <src> <dest>` | Moves or renames a file or directory |
| `Test-Path <path>` | Checks if a file or directory exists |

## 🔹 Working with Variables
| Cmdlet | Description |
|--------|-------------|
| `$var = "Hello"` | Assigns a value to a variable |
| `$var` | Retrieves the variable's value |
| `Remove-Variable var` | Deletes a variable |
| `[int]$num = 10` | Declares a typed variable |
| `$env:Path` | Shows environment variables |

## 🔹 String Manipulation
| Cmdlet | Description |
|--------|-------------|
| `$string.Length` | Gets string length |
| `$string.ToUpper()` | Converts to uppercase |
| `$string.ToLower()` | Converts to lowercase |
| `$string -replace 'old', 'new'` | Replaces text in a string |
| `$string -split ','` | Splits a string by a delimiter |

## 🔹 Loops and Conditions
### **If-Else**
```powershell
if ($var -eq 10) {
    Write-Output "Variable is 10"
} elseif ($var -gt 10) {
    Write-Output "Variable is greater than 10"
} else {
    Write-Output "Variable is less than 10"
}
```

### **For Loop**
```powershell
for ($i=1; $i -le 5; $i++) {
    Write-Output "Iteration: $i"
}
```

### **Foreach Loop**
```powershell
$items = @("apple", "banana", "cherry")
foreach ($item in $items) {
    Write-Output "Fruit: $item"
}
```

### **While Loop**
```powershell
$count = 1
while ($count -le 5) {
    Write-Output "Count: $count"
    $count++
}
```

## 🔹 Functions
```powershell
function Greet($name) {
    return "Hello, $name!"
}
Greet "John"
```

## 🔹 Managing Processes
| Cmdlet | Description |
|--------|-------------|
| `Get-Process` | Lists running processes |
| `Start-Process <exe>` | Starts a new process |
| `Stop-Process -Name <name>` | Stops a process by name |

## 🔹 Managing Users and Groups
| Cmdlet | Description |
|--------|-------------|
| `Get-LocalUser` | Lists local users |
| `New-LocalUser -Name "User" -Password (ConvertTo-SecureString "P@ssw0rd" -AsPlainText -Force) -FullName "John Doe" -Description "New user"` | Creates a new user |
| `Remove-LocalUser -Name "User"` | Deletes a user |
| `Get-LocalGroup` | Lists local groups |
| `Add-LocalGroupMember -Group "Administrators" -Member "User"` | Adds a user to a group |

## 🔹 Network Commands
| Cmdlet | Description |
|--------|-------------|
| `Test-Connection <host>` | Pings a host |
| `Get-NetAdapter` | Lists network adapters |
| `Get-NetIPAddress` | Displays IP addresses |
| `Resolve-DnsName <domain>` | Resolves a domain name |
| `Get-NetTCPConnection` | Lists active TCP connections |

## 🔹 Security & Permissions
| Cmdlet | Description |
|--------|-------------|
| `Get-Acl <file>` | Gets file permissions |
| `Set-Acl <file> <acl>` | Sets file permissions |
| `Get-ExecutionPolicy` | Shows the current script execution policy |
| `Set-ExecutionPolicy RemoteSigned` | Changes execution policy |

## 🔹 PowerShell Scripting
### **Running a Script**
```powershell
.\myscript.ps1
```

### **Handling Errors**
```powershell
Try {
    Get-Item "C:\fakepath"
} Catch {
    Write-Output "Error occurred: $_"
}
```

### **Pausing Execution**
```powershell
Start-Sleep -Seconds 5
```

## 🔹 Useful One-Liners
| Command | Description |
|---------|-------------|
| `Get-History` | Shows command history |
| `Get-Clipboard` | Retrieves clipboard contents |
| `Set-Clipboard "Hello"` | Sets clipboard contents |
| `Start-Transcript` | Logs session output |
| `Stop-Transcript` | Stops logging |
