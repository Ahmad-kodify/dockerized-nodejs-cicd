# dockerized-nodejs-CiCd

This is a simple Node.js application with Docker and Jenkins CI/CD pipeline.

## Features

- Node.js Express app running on port 3000
- Dockerized container
- Jenkins pipeline for CI/CD:
  - Checkout code
  - Install dependencies
  - Build Docker image
  - Deploy container
  - Send email notifications

## How to Run Locally

```bash
npm install
node app.js
