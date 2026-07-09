# REST API Automation Framework

This repository contains an automated end-to-end REST API testing framework for the [JSONPlaceholder](https://jsonplaceholder.typicode.com/) API. The test scripts are designed in **Postman** and executed headlessly via the command line using **Newman**.

It includes a full suite of CRUD operations (GET, POST, PUT, PATCH, DELETE) to validate the behavior of the `/posts` endpoints.

## 🎯 Key Features

- **Automated Assertions:** JavaScript test scripts validate HTTP status codes (200 OK, 201 Created), API performance metrics (response times), and payload formatting.
- **JSON Schema Validation:** Strictly enforces the expected data types and structural contract of the API response payloads.
- **CI/CD Integration:** A fully automated GitHub Actions pipeline that executes the Newman test suite on every code push.
- **Interactive Reporting:** Automatically generates and uploads rich, interactive HTML reports (`htmlextra`) as pipeline artifacts for easy stakeholder review.

## 📁 Project Structure

```text
.
├── .github/workflows/
│   └── api-tests.yml                    # GitHub Actions CI/CD pipeline configuration
├── tests/
│   ├── jsonplaceholder_collection.json  # Postman collection (Endpoints + JavaScript Assertions)
│   └── Dev.postman_environment.json     # Postman environment variables (Base URLs)
└── package.json                         # Project dependencies and Newman run scripts
```

## 🚀 Running Tests Locally

To run these tests locally and generate an interactive HTML report, you just need [Node.js](https://nodejs.org/) installed on your machine.

1. **Install dependencies:**
   ```bash
   npm install
   ```

2. **Execute the test suite:**
   ```bash
   npm run test
   ```

**Expected Output:**
Newman will execute the test suite, print a summary in your terminal window, and automatically generate a beautiful HTML report inside a newly created `newman` folder in your project directory. 

## 🔄 CI/CD Pipeline

This project utilizes **GitHub Actions** for continuous integration. Upon every push to the `main` branch, the pipeline automatically:
1. Provisions an Ubuntu runner and sets up Node.js.
2. Installs dependencies cleanly (`npm ci`).
3. Executes the Newman test suite.
4. Generates the `htmlextra` report and securely uploads it as a downloadable **Artifact** attached to the GitHub Action run.
