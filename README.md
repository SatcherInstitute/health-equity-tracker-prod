# Health Equity Tracker - Production
This repository contains the production deployment configuration and resources for the [Health Equity Tracker](https://healthequitytracker.org/) project. It serves as an extension of the main [Health Equity Tracker development repository](https://github.com/SatcherInstitute/health-equity-tracker).

## Purpose
This repository manages production-specific configurations, deployment workflows, and resources required for the live Health Equity Tracker application. By separating production concerns from the main development repository, we:
1. Manage Resources Efficiently: Prevent exhausting GitHub Actions credits on private repositories
2. Maintain Clean Separation: Keep production workflows distinct from development processes
3. Simplify Onboarding: Make it easier for new developers to understand what affects production systems
4. Reduce Code Complexity: Eliminate repetitive workflows in our main repository

## Running Production Data Pipelines
Production data pipelines (DAGs) are triggered from this repository. To run a pipeline:
1. Navigate to the Actions tab in this repository
2. Select the appropriate workflow from the list
3. Click "Run workflow" and provide any required parameters
4. Monitor the workflow execution for completion and results
   
## Getting Started
For development work, please refer to the main repository. This repository is primarily for production deployment management and running production data pipelines.

## When adding new production workflows:
1. Create your workflow file in the .github/workflows directory
2. Ensure all required secrets are available in this repository
3. Test the workflow with a manual trigger before relying on scheduled runs

## Production Release Process
The production release workflow builds and deploys the Health Equity Tracker to production. It's automatically triggered when a new release is created in the main repository.

## How It Works
A release in the main repository triggers a dispatch event to this repository
The releaseToProd.yaml workflow builds all Docker images, pushes them to GCR, and deploys them using Terraform

## Manually Triggering a Release
Go to Actions → Release to Production → Click "Run workflow" → Enter: Release Version for Production -> Click "Run workflow"
