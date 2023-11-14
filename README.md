# OpenIMIS Dynamic Application Security Testing

This repository contains the workflow for building and scanning the openIMIS Dockerized application, leveraging GitHub Actions for continuous integration and security checks.

## Overview

The workflow automates the following processes:
1. **Building the openIMIS Application**: Clones and sets up the openIMIS application from the `openimis/openimis-dist_dkr` repository.
2. **Docker Environment Setup**: Configures the Docker environment by creating necessary `.env` files and running Docker Compose.
3. **Security Scanning with OWASP ZAP**: Performs automated security scans on the application using OWASP ZAP to ensure the application's security posture.

## Workflow Details

### Building the openIMIS Application

The GitHub Actions workflow begins by cloning the `openimis/openimis-dist_dkr` repository from the `develop` branch. This step ensures that the latest version of the application is used for the build and subsequent scanning.

### Docker Environment Setup

After cloning the repository, the workflow sets up the Docker environment. It involves copying the `.env.example` file to a `.env` file and running `docker-compose up -d`. This step is crucial for creating a proper environment for the application to run.

### Security Scanning with OWASP ZAP

The final step of the workflow is to perform a security scan using OWASP ZAP. This step is vital to identify potential security vulnerabilities within the application. The scan targets `http://localhost:80`, assuming the application is exposed on port 80.

## Running the Workflow

The workflow is configured to run under the following conditions:
- **On Push to Main Branch**: Triggers whenever changes are pushed to the `main` branch.
- **Manual Trigger**: Can be manually triggered from the GitHub Actions tab for ad-hoc scanning.
- **Scheduled Runs**: Automatically runs once a day at midnight UTC.

## Conclusion

This automated workflow is a significant step towards ensuring the continuous integration and security of the openIMIS Dockerized application. It simplifies the process of deployment and routine security checks, making the development cycle more efficient and secure.