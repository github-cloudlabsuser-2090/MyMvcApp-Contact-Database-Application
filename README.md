# MyMvcApp-Contact-Databse-Application

# MyMvcApp CRUD Application Deployment Guide

## Overview
This guide provides instructions for deploying the MyMvcApp CRUD Application to Azure using an ARM template and GitHub Actions.

## Steps to Deploy

### 1. Create Azure Resources
- The ARM template (`deploy.json`) defines the following resources:
  - Azure Web App
  - App Service Plan
- The parameters file (`deploy.parameters.json`) provides values for the template parameters.

### 2. Configure GitHub Actions Workflow
- The GitHub Actions workflow (`.github/workflows/azure-deploy.yml`) automates the deployment process.
- Ensure the following secrets are configured in your GitHub repository:
  - `AZURE_CREDENTIALS`: Azure service principal credentials.
  - `AZURE_WEBAPP_PUBLISH_PROFILE`: Publish profile for the Azure Web App.

### 3. Validate and Deploy
- Push the changes to the `master` branch to trigger the GitHub Actions pipeline.
- The pipeline will:
  1. Build the application using `dotnet publish`.
  2. Deploy the application to the Azure Web App.

### 4. Verify Deployment
- Access the application using the Azure Web App's default domain.
- Ensure the application is functioning as expected.

## File Structure
- `deploy.json`: ARM template for Azure resources.
- `deploy.parameters.json`: Parameters for the ARM template.
- `.github/workflows/azure-deploy.yml`: GitHub Actions workflow for deployment.

## Notes
- Update the `appServicePlanId` in `deploy.parameters.json` with your Azure subscription and resource group details.
- Ensure the path in the workflow file is correct for the `dotnet publish` and `Upload artifact for deployment` steps.

## Troubleshooting
- Check the GitHub Actions logs for errors during the build or deployment process.
- Validate the ARM template and parameters file using Azure CLI or the Azure portal.
