
# 🔧 Ansible Comprehensive Cheatsheet

## 🔹 Introduction
Ansible is an open-source **automation tool** written in Python, used for **configuration management**, **application deployment**, and **orchestration**. It is **agentless** and uses **SSH** to connect to remote machines.

---

## 🔹 Installing Ansible
```sh
# On Ubuntu/Debian
sudo apt update && sudo apt install ansible -y

# On macOS (using Homebrew)
brew install ansible

# Using pip (for any OS with Python)
pip install ansible

# Verify installation
ansible --version
```

---

## 🔹 Ansible Inventory
### ✅ Define an Inventory File (`inventory.ini`)
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

# Execute a shell command
ansible all -m command -a "uptime"

# Install a package (Debian-based systems)
ansible webservers -m apt -a "name=nginx state=present update_cache=true" --become

# Copy a file
ansible all -m copy -a "src=./index.html dest=/var/www/html/index.html" --become

# Reboot a host
ansible all -m reboot --become
```

---

## 🔹 Writing an Ansible Playbook
### ✅ Sample `playbook.yml`
```yaml
- name: Deploy Web Server
  hosts: webservers
  become: yes
  tasks:
    - name: Install Nginx
      apt:
        name: nginx
        state: present
        update_cache: yes

    - name: Copy Index File
      copy:
        src: ./index.html
        dest: /var/www/html/index.html

    - name: Start Nginx Service
      service:
        name: nginx
        state: started
        enabled: true
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
index_file: ./index.html
```

### 📌 Use Variables in Playbook
```yaml
- name: Install Web Server with Variables
  hosts: webservers
  become: yes
  vars_files:
    - vars.yml
  tasks:
    - name: Install Web Package
      apt:
        name: "{{ web_package }}"
        state: present

    - name: Deploy Index File
      copy:
        src: "{{ index_file }}"
        dest: /var/www/html/index.html
```

---

## 🔹 Ansible Handlers
```yaml
- name: Configure and restart Nginx
  hosts: webservers
  become: yes
  tasks:
    - name: Replace nginx config
      copy:
        src: nginx.conf
        dest: /etc/nginx/nginx.conf
      notify: restart nginx

  handlers:
    - name: restart nginx
      service:
        name: nginx
        state: restarted
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
 │   └── main.yml
 ├── handlers/
 │   └── main.yml
 ├── templates/
 ├── files/
 ├── vars/
 ├── defaults/
 ├── meta/
```

### 📌 Use a Role in Playbook
```yaml
- name: Deploy App using Role
  hosts: webservers
  become: yes
  roles:
    - my_role
```

---

## 🔹 Templates with Jinja2
```yaml
- name: Deploy Config Template
  template:
    src: nginx.conf.j2
    dest: /etc/nginx/nginx.conf
  notify: restart nginx
```

---

## 🔹 Useful Playbook Flags
```sh
# Check syntax
ansible-playbook playbook.yml --syntax-check

# Dry run (no changes made)
ansible-playbook playbook.yml --check

# Verbose output
ansible-playbook playbook.yml -v
```

---

## 🔹 Ansible Best Practices
- ✅ **Use inventory files** to manage host groups clearly.
- ✅ **Keep playbooks modular** by using **roles** and **handlers**.
- ✅ **Store variables** in separate files (e.g., `vars.yml`, `group_vars/`).
- ✅ **Use `templates/`** with Jinja2 for config files.
- ✅ **Test your playbooks** with `--check` and `ansible-lint`.
- ✅ **Avoid hardcoding values** — always use variables.
