# 🚀 GitHub/GitLab Advanced Features Cheatsheet

## 🔹 Introduction
GitHub and GitLab provide **advanced features** beyond basic Git operations, including **CI/CD, issue tracking, project management, and security scanning**.

---

## 🔹 Forking & Pull Requests (GitHub) / Merge Requests (GitLab)
### ✅ Fork a Repository
```sh
# Clone the forked repository
git clone https://github.com/your-username/repo.git
```

### ✅ Create a Pull Request (GitHub) / Merge Request (GitLab)
1. **Create a new branch**
   ```sh
   git checkout -b feature-branch
   ```
2. **Make changes & push the branch**
   ```sh
   git add .
   git commit -m "Added new feature"
   git push origin feature-branch
   ```
3. **Open a Pull Request (GitHub) / Merge Request (GitLab)**
   - Go to the repository → **Pull Requests** (GitHub) / **Merge Requests** (GitLab)
   - Click **New Pull/Merge Request**
   - Compare changes and submit for review

---

## 🔹 GitHub Actions (CI/CD)
### ✅ Create a GitHub Actions Workflow
1. Create a `.github/workflows/ci.yml` file.
2. Define the workflow:
   ```yaml
   name: CI Pipeline
   on: [push, pull_request]
   jobs:
     build:
       runs-on: ubuntu-latest
       steps:
         - uses: actions/checkout@v2
         - name: Install Dependencies
           run: npm install
         - name: Run Tests
           run: npm test
   ```
3. Commit and push the workflow. It will **automatically run on new commits**.

---

## 🔹 GitLab CI/CD Pipelines
### ✅ Create a `.gitlab-ci.yml` File
```yaml
stages:
  - build
  - test
  - deploy

build:
  stage: build
  script:
    - npm install

test:
  stage: test
  script:
    - npm test

deploy:
  stage: deploy
  script:
    - echo "Deploying application"
```

### ✅ Run the Pipeline
- **Push changes**, and the pipeline **runs automatically**.
- Monitor the pipeline under **CI/CD > Pipelines** in GitLab.

---

## 🔹 Issue Tracking & Project Management
### ✅ Create an Issue
- **GitHub:** Go to **Issues** → Click **New Issue**.
- **GitLab:** Go to **Issues** → Click **New Issue**.

### ✅ Assign & Label Issues
```sh
# Assign an issue to a user
git issue assign @username

# Add a label
git issue label bug
```

### ✅ GitHub Project Boards
- Use **Kanban-style boards** under **Projects**.
- **Drag & drop issues** into **To Do, In Progress, and Done** columns.

### ✅ GitLab Epics & Milestones
- **Epics**: Track long-term goals.
- **Milestones**: Group issues by deadlines.

---

## 🔹 Security & Code Analysis
### ✅ GitHub Dependabot (Automatic Security Fixes)
- **Enable Dependabot** in **Security > Dependabot Alerts**.
- **Automatically updates dependencies** in `package.json`, `requirements.txt`, etc.

### ✅ GitLab Security Scanning
- **Enable SAST (Static Application Security Testing)** under **Security & Compliance**.
- **Run a security scan** in `.gitlab-ci.yml`:
  ```yaml
  sast:
    stage: test
    script:
      - echo "Running Security Scan"
  ```

---

## 🔹 Best Practices
- **Use CI/CD pipelines** to automate testing & deployments.
- **Follow branching strategies** (e.g., Git Flow, Feature Branching).
- **Enable security scans** to detect vulnerabilities early.
- **Use GitHub Actions/GitLab CI** for automated workflows.
- **Use project management tools** (Issues, Milestones, Boards) for effective collaboration.

---