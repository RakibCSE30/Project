# CI/CD Deployment Pipeline

The **Smart Question Bank** project utilizes **GitHub Actions** to automate automated testing, linting, and continuous delivery to staging/production environments.

---

## 1. Workflow Architecture

Every time a developer interacts with the GitHub repository, the pipeline runs automated checks based on the target branch:

---

## 2. Continuous Integration (CI) Checks

On every **Pull Request (PR)** submitted against the `main` branch, the following automated workflow triggers instantly:

1. **Environment Setup:** Spins up a fresh Ubuntu container running Node.js v20.
2. **Dependency Installation:** Runs `npm ci` to cleanly install required packages.
3. **Linting Verification:** Executes `npm run lint` to check for coding standard violations.
4. **Test Execution:** Runs `npm run test` to verify no existing features are broken.

> 🛑 **Hard Rule:** A Pull Request **cannot** be merged into the `main` branch if any of the CI pipeline stages fail.

---

## 3. GitHub Actions Configuration (`.github/workflows/ci.yml`)

For your reference, here is the automated configuration script running in our backend:

```yaml
name: Node.js CI

on:
  push:
    branches: [ "main" ]
  pull_request:
    branches: [ "main" ]

jobs:
  build_and_test:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout repository
      uses: actions/checkout@v4

    - name: Setup Node.js
      uses: actions/setup-node@v4
      with:
        node-version: '20.x'
        cache: 'npm'

    - name: Install dependencies
      run: npm ci

    - name: Run Linter
      run: npm run lint --if-present

    - name: Execute Unit Tests
      run: npm test