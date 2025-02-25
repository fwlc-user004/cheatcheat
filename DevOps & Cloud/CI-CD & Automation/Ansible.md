# 🔧 Ansible Comprehensive Cheatsheet

## 🔹 Introduction
Ansible is an open-source **automation tool** used for **configuration management**, **application deployment**, and **orchestration**.

---

## 🔹 Installing Ansible
```sh
# Install Ansible on Ubuntu/Debian
sudo apt update && sudo apt install ansible -y

# Install Ansible on macOS
brew install ansible

# Check installed version
ansible --version
```

---

## 🔹 Ansible Inventory
### ✅ Define an inventory file (`inventory.ini`)
```ini
[webservers]
web1 ansible_host=192.168.1.10 ansible_user=ubuntu
web2 ansible_host=192.168.1.11 ansible_user=ubuntu

[databases]
db1 ansible_host=192.168.1.20 ansible_user=root
```

### 📌 List Hosts
```sh
ansible all --list-hosts
```

---

## 🔹 Running Ad-Hoc Commands
```sh
# Ping all hosts
ansible all -m ping

# Execute a command
ansible all -m command -a "uptime"

# Install a package
ansible webservers -m apt -a "name=nginx state=present" --become
```

---

## 🔹 Writing an Ansible Playbook
### ✅ Create `playbook.yml`
```yaml
- name: Deploy Web Server
  hosts: webservers
  become: yes
  tasks:
    - name: Install Nginx
      apt:
        name: nginx
        state: present

    - name: Start Nginx Service
      service:
        name: nginx
        state: started
```

### 📌 Run the Playbook
```sh
ansible-playbook playbook.yml
```

---

## 🔹 Variables in Ansible
### ✅ Define Variables in `vars.yml`
```yaml
web_package: nginx
```

### 📌 Use Variables in Playbook
```yaml
- name: Install Web Server
  hosts: webservers
  become: yes
  vars_files:
    - vars.yml
  tasks:
    - name: Install Web Package
      apt:
        name: "{{ web_package }}"
        state: present
```

---

## 🔹 Ansible Roles
### ✅ Create a Role
```sh
ansible-galaxy init my_role
```

### 📌 Directory Structure
```plaintext
my_role/
 ├── tasks/
 │   ├── main.yml
 ├── handlers/
 │   ├── main.yml
 ├── templates/
 ├── files/
 ├── vars/
 ├── defaults/
 ├── meta/
```

### 📌 Use a Role in Playbook
```yaml
- name: Deploy Application
  hosts: webservers
  roles:
    - my_role
```

---

## 🔹 Ansible Best Practices
- **Use inventory files** for better host management.
- **Use variables and templates** to keep playbooks dynamic.
- **Keep tasks modular** by using **roles**.
- **Test playbooks** using **ansible-lint** before execution.
- **Use handlers** to restart services only when needed.

---