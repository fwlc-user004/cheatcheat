# 🖥️ Virtual Machines (VMWare, VirtualBox, KVM) Comprehensive Cheatsheet

## 🔹 Introduction
Virtual Machines (VMs) allow users to **run multiple operating systems** on a single physical machine by using a hypervisor. The three most common hypervisors are:
- **VMWare** (Commercial, Feature-Rich)
- **VirtualBox** (Free & Open-Source, Cross-Platform)
- **KVM** (Linux Kernel-based Virtual Machine, Native Linux Support)

---

## 🔹 VMWare
### ✅ Installation
```sh
# Install VMWare Workstation on Ubuntu
sudo apt install vmware-workstation
```

### 📌 Basic Commands
```sh
# Start a VM
vmrun start /path/to/your/vm.vmx

# Stop a VM
vmrun stop /path/to/your/vm.vmx

# List all VMs
vmrun list
```

### 📌 Snapshots
```sh
# Create a snapshot
vmrun snapshot /path/to/your/vm.vmx snapshot_name

# Revert to a snapshot
vmrun revertToSnapshot /path/to/your/vm.vmx snapshot_name
```

---

## 🔹 VirtualBox
### ✅ Installation
```sh
# Install VirtualBox on Ubuntu
sudo apt install virtualbox

# Install VirtualBox on macOS
brew install --cask virtualbox
```

### 📌 Basic Commands
```sh
# List all VMs
VBoxManage list vms

# Start a VM
VBoxManage startvm "VM Name"

# Stop a VM
VBoxManage controlvm "VM Name" poweroff
```

### 📌 Snapshots
```sh
# Create a snapshot
VBoxManage snapshot "VM Name" take "Snapshot Name"

# Restore a snapshot
VBoxManage snapshot "VM Name" restore "Snapshot Name"
```

---

## 🔹 KVM (Kernel-based Virtual Machine)
### ✅ Installation
```sh
# Install KVM and dependencies on Ubuntu
sudo apt install qemu-kvm libvirt-daemon-system virt-manager
```

### 📌 Basic Commands
```sh
# List available VMs
virsh list --all

# Start a VM
virsh start vm_name

# Stop a VM
virsh shutdown vm_name
```

### 📌 Snapshots
```sh
# Create a snapshot
virsh snapshot-create-as --domain vm_name --name snapshot_name

# Restore a snapshot
virsh snapshot-revert vm_name --snapshotname snapshot_name
```

---

## 🔹 Networking in VMs
### ✅ Bridged Networking (VM Uses Host Network)
- **VMWare**: Enable **Bridged Mode** in network settings.
- **VirtualBox**: Set **Adapter 1** to **Bridged Adapter**.
- **KVM**: Use `virsh net-start default` for a default network bridge.

### ✅ NAT Networking (VM Accesses Internet, No Direct Access)
- Default for most hypervisors.
- Use port forwarding for external access.

---

## 🔹 VM Best Practices
- **Allocate sufficient CPU & RAM** for performance.
- **Use snapshots before making major changes.**
- **Enable Guest Additions/Tools** for better integration.
- **Use SSD storage** for faster VM performance.
- **Secure VMs** by restricting unnecessary network access.

---