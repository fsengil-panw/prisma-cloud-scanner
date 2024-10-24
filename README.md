# Scan Container Image with Prisma Cloud

This repository contains a GitHub Actions workflow that allows you to scan a container image using Prisma Cloud. Follow the steps below to fork the repository, add the necessary secrets, and run the workflow manually.

## Prerequisites

- **Prisma Cloud Compute Account**: Ensure you have access to [Prisma Cloud Compute](https://www.paloaltonetworks.com/prisma/cloud) with API credentials.
- **Docker Image**: Have the container image you want to scan available (e.g., `nginx:latest`).

## Steps

### 1. Fork the Repository

1. **Navigate to the Repository**: Visit the GitHub repository containing the workflow.
2. **Fork the Repository**: Click on the **Fork** button at the top-right corner to create a copy under your GitHub account.

### 2. Add Secrets to Your Repository

The workflow requires certain secrets to authenticate with Prisma Cloud. You'll need to add these to your forked repository.

1. **Go to Settings**: In your repository, click on the **Settings** tab.
2. **Access Secrets**:
   - In the left sidebar, select **Secrets and variables**.
   - Click on **Actions**.
3. **Add New Repository Secrets**: Click on **New repository secret** for each secret below:

   - `PRISMA_API_URL`: Your Prisma Cloud API URL.
   - `PRISMA_ACCESS_KEY`: Your Prisma Cloud Access Key.
   - `PRISMA_SECRET_KEY`: Your Prisma Cloud Secret Key.
   - `PRISMA_COMPUTE_URL`: Your Prisma Cloud Compute Console URL.

   **Example**:

   - **Name**: `PRISMA_API_URL`
   - **Value**: `https://api.prismacloud.io`

4. **Save Each Secret**: After entering the name and value, click **Add secret**.

### 3. Run the Workflow Manually

1. **Navigate to Actions**: Click on the **Actions** tab in your repository.
2. **Select the Workflow**: Choose **Scan Container Image with Prisma Cloud** from the list.
3. **Run the Workflow**:
   - Click on **Run workflow** on the right side.
   - Fill in the required inputs:
     - **container_image**: *(Required)* The Docker image to scan (e.g., `nginx:latest`).
     - **container_env_variables**: *(Optional)* Environment variables (e.g., `-e "ENV_VAR=value"`).
     - **container_app**: *(Optional)* Command to start the application inside the container.
   - Click **Run workflow** to start the process.

### 4. Monitor the Workflow

- **View Progress**: The workflow run will appear under **Workflow runs**.
- **Check Details**: Click on the running workflow to see logs and outputs of each step.

## Workflow Overview

The GitHub Actions workflow performs the following steps:

1. **Pull Docker Image**: Pulls the specified Docker image.
2. **Prisma Cloud Scan**: Scans the image using Prisma Cloud's scanning tools.
3. **Download Twistcli**: Downloads the `twistcli` utility for scanning.
4. **Scan for Vulnerabilities**: Performs a detailed vulnerability scan using `twistcli`.
5. **Sandbox Analysis**: Runs the container in a sandbox for dynamic analysis.

