# 🚀 GitLab CI/CD Comprehensive Cheatsheet

## 🔹 Introduction
GitLab CI/CD automates testing, building, and deployment in **GitLab repositories** using `.gitlab-ci.yml`.

---

## 🔹 Setting Up GitLab CI/CD
### ✅ Create `.gitlab-ci.yml` in Repository
```yaml
stages:
  - build
  - test
  - deploy
```

---

## 🔹 Defining Jobs
```yaml
build:
  stage: build
  script:
    - echo "Building the project"
```

```yaml
test:
  stage: test
  script:
    - echo "Running tests"
```

```yaml
deploy:
  stage: deploy
  script:
    - echo "Deploying the application"
```

---

## 🔹 Pipeline Triggers
```yaml
# Run CI/CD on every push to the main branch
only:
  - main
```

```yaml
# Run CI/CD on merge requests
workflow:
  rules:
    - if: "$CI_PIPELINE_SOURCE == 'merge_request_event'"
```

---

## 🔹 Caching Dependencies
```yaml
cache:
  key: ${CI_COMMIT_REF_SLUG}
  paths:
    - node_modules/
```

---

## 🔹 Artifacts (Save Files Between Stages)
```yaml
artifacts:
  paths:
    - dist/
  expire_in: 1 hour
```

---

## 🔹 Running Jobs in Parallel
```yaml
test1:
  stage: test
  script: echo "Running test 1"

test2:
  stage: test
  script: echo "Running test 2"
```

---

## 🔹 Deploying to Production
```yaml
deploy:
  stage: deploy
  script:
    - echo "Deploying..."
  environment:
    name: production
    url: https://myapp.com
```

---

## 🔹 Using Secrets & Environment Variables
```yaml
variables:
  API_KEY: "${CI_API_KEY}"
```

```yaml
deploy:
  script:
    - echo "Using API Key: $API_KEY"
  only:
    - main
```

---

## 🔹 Scheduled Pipelines (CRON Jobs)
```yaml
workflow:
  rules:
    - if: "$CI_PIPELINE_SOURCE == 'schedule'"
```

---

## 🔹 GitLab CI/CD Best Practices
- **Use caching** to reduce build times.
- **Minimize pipeline complexity** to keep execution efficient.
- **Store secrets securely** in GitLab CI/CD variables.
- **Use parallel jobs** to speed up test execution.
- **Deploy only on `main` or `release` branches** to avoid accidental deployments.

---
