---
title: Azure Pipelines vs GitHub Actions v1
author: jamey
descrition: Reference for Azure Pipelines vs GitHub Actions
date: 2025-11-8 07:40:00 -0300
tags:
  - az400
  - azure devops
  - pipelines
  - azure pipelines
  - devops
  - ci/cd
---

# Azure DevOps (ADO) to GitHub Actions: Direct 1:1 Mapping

Here's the **direct 1:1 mapping** from Azure DevOps (ADO) Pipelines to GitHub Actions:

| ADO concept | GitHub Actions equivalent | What it does | YAML key |
|-------------|---------------------------|--------------|----------|
| **Pipeline** | **Workflow** | The whole CI/CD file that runs on a trigger | `.github/workflows/your-name.yml` |
| **Stage** | **Separate workflow file** (or `needs:` + reusable workflows) | Logical phase (build → test → deploy). No built-in `stages:` keyword. Chain workflows with `workflow_run` or `needs:`. | `jobs:<job>.needs:` |
| **Job** | **Job** | Unit of work that gets its own runner (VM/container) | `jobs:<job_id>:` |
| **Task** | **Action** (or script step) | Reusable building block (`PublishTestResults@2` → `actions/upload-artifact@v4`) | `uses: owner/action@vX` |
| **Step** | **Step** | One command or one action inside a job | `steps:` list |

---

## Quick Side-by-Side Example

### ADO (YAML)

```yaml
stages:
- stage: Build
  jobs:
  - job: Compile
    steps:
    - task: DotNetCoreCLI@2   # ← task
      inputs:
        command: build
    - script: echo Hello     # ← script step

- stage: Deploy
  dependsOn: Build
  jobs:
  - job: AzureWebApp
    steps:
    - task: AzureWebApp@1
      inputs:
        appName: 'my-app'
```

### GitHub Actions (YAML)

```yaml
name: CI/CD Pipeline
on:
  push:
    branches:
      - main
jobs:
  Compile:
    runs-on: ubuntu-latest
    steps:
    - name: Build .NET Core   # ← action
      uses: actions/setup-dotnet@v3
      with:
        dotnet-version: '6.0.x'
    - name: Echo Hello        # ← script step
      run: echo Hello
  AzureWebApp:
    needs: Compile
    runs-on: ubuntu-latest
    steps:
    - name: Deploy to Azure Web App
      uses: azure/webapps-deploy@v2
      with:
        app-name: 'my-app'
```

## Summary Mapping

```yaml
ADO pipeline → GitHub Actions
ADO pipeline → .github/workflows/your-workflow.yml
ADO stage  → split into separate workflow files
ADO job    → jobs: myjob:
ADO task   → uses: some/action@v4
ADO step   → steps:
               - run: echo hello
               - uses: actions/checkout@v4
```

