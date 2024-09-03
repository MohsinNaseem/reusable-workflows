# GitHub Actions Reusable Workflows

This repository provides a collection of reusable GitHub Actions workflows designed to streamline the development, testing, and deployment processes for Java Spring applications and Terraform-managed infrastructure. These workflows can be easily integrated into your GitHub repositories to automate key tasks, ensuring consistency and efficiency across various environments.

The workflows are categorized into the following main sections:

## Table of Contents

- [Build and Deploy Pipeline](#build-and-deploy-pipeline)
- [Pull Request Validation Pipeline](#pr-validation-pipeline)
- [Terraform Destroy](#terraform-destroy)
- [Terraform Plan and Apply](#terraform-plan-and-apply)

Each section includes a detailed description of the workflow, its usage, and how it can be customized to fit different environments and requirements.

## Build and Deploy Pipeline

**File:** `.github/workflows/build-deploy-pipeline.yaml`

This workflow automates the process of building, testing, and deploying Java Spring applications. It is designed to handle deployments across various environments such as development, staging, and production.

### Usage

To integrate this workflow into your project, create a new workflow file in your repository's `.github/workflows` directory and reference the reusable workflow as shown below:

```yaml
name: Build and Deploy

on:
  push:
    branches:
      - main

jobs:
  java-pipeline:
    name: "Java Maven CI/CD Pipeline"
    uses: MohsinNaseem/reusable-workflows/.github/workflows/build-deploy-pipeline.yaml@main
    with:
      environment: ${{ github.event.inputs.environment }}
      main-repo: ${{ github.event.repository.name }}
      account-id: "XXXXXXXXX"
    secrets: inherit
