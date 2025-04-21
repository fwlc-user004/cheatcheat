
# 🚀 GitHub Actions Comprehensive Cheatsheet

## 🔹 Introduction
GitHub Actions is a **CI/CD** tool that allows you to **automate, customize, and execute software development workflows** directly in your GitHub repository.

- Each workflow is defined in a `.yml` file inside the `.github/workflows/` directory.
- GitHub Actions supports **Linux, macOS, and Windows runners**.
- Workflows are triggered by **events** like push, pull requests, schedule, issue creation, and more.

---

## 🔹 Setting Up a Workflow
### ✅ Create a Workflow File
Create a file at `.github/workflows/main.yml`.

```yaml
name: CI Pipeline

on: [push, pull_request]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout Repository
        uses: actions/checkout@v3

      - name: Set up Node.js
        uses: actions/setup-node@v3
        with:
          node-version: '16'

      - name: Install Dependencies
        run: npm install

      - name: Run Tests
        run: npm test
```

---

## 🔹 Workflow Triggers
```yaml
on:
  push:
    branches:
      - main
  pull_request:
    branches:
      - main
  schedule:
    - cron: '0 0 * * *'  # every day at midnight UTC
  workflow_dispatch:     # manual trigger via GitHub UI
```

---

## 🔹 Common Jobs & Steps

### ✅ Using Different Runners
```yaml
jobs:
  build:
    runs-on: ubuntu-latest  # or windows-latest, macos-latest
```

### ✅ Matrix Builds
```yaml
jobs:
  test:
    runs-on: ubuntu-latest
    strategy:
      matrix:
        node: [14, 16, 18]  # multiple Node.js versions
    steps:
      - uses: actions/checkout@v3
      - name: Setup Node.js
        uses: actions/setup-node@v3
        with:
          node-version: ${{ matrix.node }}
      - run: npm install && npm test
```

---

## 🔹 Caching Dependencies
```yaml
- name: Cache Dependencies
  uses: actions/cache@v3
  with:
    path: ~/.npm
    key: npm-${{ runner.os }}-${{ hashFiles('**/package-lock.json') }}
    restore-keys: |
      npm-${{ runner.os }}-
```

---

## 🔹 Deployments

### ✅ Deploy to GitHub Pages
```yaml
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Build Site
        run: npm run build
      - name: Deploy to GitHub Pages
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./build
```

### ✅ Deploy to AWS S3
```yaml
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Upload to S3
        uses: jakejarvis/s3-sync-action@v0.5.1
        with:
          args: --acl public-read --follow-symlinks --delete
        env:
          AWS_S3_BUCKET: ${{ secrets.AWS_S3_BUCKET }}
          AWS_ACCESS_KEY_ID: ${{ secrets.AWS_ACCESS_KEY_ID }}
          AWS_SECRET_ACCESS_KEY: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
```

---

## 🔹 Secrets & Environment Variables
```yaml
env:
  DATABASE_URL: ${{ secrets.DATABASE_URL }}
  NODE_ENV: production
```

---

## 🔹 Reusable Workflows (Advanced)
```yaml
# caller.yml
jobs:
  call-workflow:
    uses: ./.github/workflows/deploy.yml
    with:
      node-version: 18
```

---

## 🔹 GitHub Actions Best Practices
- ✅ **Use caching** to speed up builds and reduce CI time.
- ✅ **Use matrix strategy** to test on multiple environments.
- ✅ **Secure your credentials** with GitHub `secrets`.
- ✅ **Keep workflows small** and modular for clarity and performance.
- ✅ **Lint your YAML files** to catch syntax errors early.
- ✅ **Use reusable workflows** to avoid repetition.
- ✅ **Test workflows** using `act` (a local testing tool).



