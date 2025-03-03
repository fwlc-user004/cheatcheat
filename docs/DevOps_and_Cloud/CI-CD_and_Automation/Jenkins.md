# 🚀 Jenkins Comprehensive Cheatsheet

## 🔹 Introduction
Jenkins is an open-source automation server used for **CI/CD pipelines**, **automated testing**, and **deployment**.

---

## 🔹 Installing Jenkins
```sh
# Install Jenkins on Ubuntu
sudo apt update && sudo apt install jenkins

# Start Jenkins service
sudo systemctl start jenkins

# Check Jenkins status
sudo systemctl status jenkins

# Access Jenkins web UI
http://localhost:8080
```

---

## 🔹 Creating a Jenkins Pipeline
### ✅ Define a `Jenkinsfile`
```groovy
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building the project...'
            }
        }
        stage('Test') {
            steps {
                echo 'Running tests...'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying the application...'
            }
        }
    }
}
```

---

## 🔹 Jenkins Pipeline Triggers
```groovy
pipeline {
    triggers {
        pollSCM('H/5 * * * *') // Check for changes every 5 minutes
    }
}
```

---

## 🔹 Environment Variables
```groovy
environment {
    MY_VAR = 'production'
}
stages {
    stage('Print Environment Variable') {
        steps {
            echo "Environment: ${MY_VAR}"
        }
    }
}
```

---

## 🔹 Running Shell Commands in Jenkins
```groovy
stage('Run Shell Command') {
    steps {
        sh 'echo Hello from Shell!'
    }
}
```

---

## 🔹 Jenkins Plugins Management
```sh
# List installed plugins
jenkins-cli list-plugins

# Install a new plugin
jenkins-cli install-plugin github

# Restart Jenkins after installing plugins
sudo systemctl restart jenkins
```

---

## 🔹 Secure Jenkins
```sh
# Create an admin user in Jenkins
http://localhost:8080 -> Manage Jenkins -> Configure Global Security

# Enable authentication and authorization
Manage Jenkins -> Configure Global Security -> Enable Security
```

---

## 🔹 Jenkins Best Practices
- **Use pipelines instead of freestyle jobs** for flexibility.
- **Use Jenkins credentials** to store secrets securely.
- **Keep Jenkins updated** for security fixes.
- **Run Jenkins inside a Docker container** for portability.
- **Use Jenkins agents** to distribute builds across multiple machines.

---