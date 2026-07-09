# JSONPlaceholder API Testing Project

This repository contains automated API tests for the [JSONPlaceholder](https://jsonplaceholder.typicode.com/) mock API. The tests are written using **Postman** and can be executed via the command line using **Newman**.

It includes a full suite of CRUD operations (GET, POST, PUT, PATCH, DELETE) to validate the behavior of the `/posts` endpoints. 

## 📁 Project Structure

```text
.
└── tests/
    ├── jsonplaceholder_collection.json  # The Postman collection containing all requests and test scripts
    └── Dev.postman_environment.json     # The Postman environment variables (e.g., base URLs)
```

## 🚀 Prerequisites

To run these tests locally, you will need:
- [Node.js](https://nodejs.org/) (which includes `npm` or `npx`)

## 💻 Running Tests Locally

You can run the tests directly from your terminal using `npx` (which will temporarily download and run Newman without needing a global installation):

```bash
# Run tests using Newman
npx newman run tests/jsonplaceholder_collection.json -e tests/Dev.postman_environment.json
```

**Expected Output:**
You should see a CLI output detailing the execution of the requests, their status codes, and test assertions (e.g., Response time checks, JSON validation).

## 🔄 CI/CD Integration

This project is integrated with continuous integration/continuous deployment (CI/CD) pipelines (e.g., GitHub Actions). The pipeline is configured to automatically run the Newman test suite on every push or pull request to the `main` branch. 

This ensures that any changes to the API or the test suite itself are constantly validated, maintaining the integrity of our endpoints.

## 📊 Generating HTML Reports (Optional)

If you'd like to view a detailed HTML report of your test runs locally, you can use the `newman-reporter-htmlextra` package:

```bash
# Install the HTML reporter
npm install -g newman-reporter-htmlextra

# Run tests and generate the report
npx newman run tests/jsonplaceholder_collection.json -e tests/Dev.postman_environment.json -r htmlextra,cli
```
*This will create a `newman` folder in your project directory containing a stylish HTML report of the test results.*
