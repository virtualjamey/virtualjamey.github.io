---
title: GitHub Actions Basics
description: Basics of GitHub Actions
date: 2025-02-03 13:40:00 -0300
# image:
#   path: "/assets/img/posts/wall.png"
#   alt: "Breaking Through The Wall"
category:
 - github
 - actions
 - ci/cd
 - devops
 - fundamentals
tags:
  - github
  - actions
  - ci/cd
  - devops
  - fundamentals
---

## What are GitHub Actions?

GitHub Actions is a continuous integration and continuous deployment (CI/CD) service provided by GitHub that allows you to automate your software development workflows. With GitHub Actions, you can create custom workflows that build, test, package, release, and deploy your code directly from your GitHub repository. 

## GitHub Actions Concepts

GitHub Actions Workflows are defined using YAML files that specify the actions, triggers, and conditions for running the automation. The workflow is defined by a YAML file in the `.github/workflows` directory of your repository. 

The following are some key concepts in GitHub Actions:

- **Workflow**: A set of rules and steps that define the automation process.
- **Event**: The trigger that starts the workflow, such as a push to a repository, a pull request, or a scheduled event.
- **Job**: A set of steps that execute on the same runner.
- **Runner**: The server that executes the job's steps.
- **Step**: A single task that can run commands or actions.
- **Action**: A reusable unit of code that can be used in multiple workflows.
- **Environment**: A set of environment variables that can be used in the workflow.
- **Secret**: Encrypted variables that are stored in the repository or organization settings.
- **Artifact**: A file or collection of files produced by a workflow that can be used in other workflows.

### Example Workflow

Below is a simple example of a GitHub Actions workflow that checks out code from my repository, setups up terraform, runs terraform apply and uploads an artifact. The comments in the YAML file explain each part of the workflow:

```yaml
# Workflow name
name: CI

# Event that triggers the workflow
on: [push, pull_request]

# Jobs to run as part of the workflow
jobs:

# Job name
  build:

    # Runner to use
    runs-on: ubuntu-latest
    
    # Steps to run as part of the job
    steps:
    
    # Step name
    - name: Checkout code
      # Action to use
      uses: actions/checkout@v2
    
    # Step name
    - name: Set up Terraform
      # Action to use
      uses: hashicorp/setup-terraform@v3
      # Action input
      with:
        # Read secret from GitHub repository using secrets.TF_API_TOKEN Note: TF_API_TOKEN is a secret stored in the repository settings.
        cli_config_credentials_token: ${{ secrets.TF_API_TOKEN }}
    
    # Step name
    - name: Terraform apply
      # Environment variables to set
      env:
        # Set environment variable with secret value
        TF_VAR_cloudflare_api_token: ${{ secrets.TF_CLOUDFLARE_KEY }}
      # Command to run
      run: terraform apply -auto-approve -no-color
    
    # Step name
    - name: Artifact
      # Upload artifact
      uses: actions/upload-artifact@v2
      # Upload artifact
      with:
        # Artifact name
        name: artifact
        # Path to the artifact
        path: | 
          build/file.yaml
```

## GitHub Actions Steps

In GitHub Actions, a step is a unit of execution within a job. Steps define what actions to take, such as running scripts, using pre-built actions, or setting environment variables. Each step can have various options that control its behavior. Steps are the are where the real **"Action"** happens in a GitHub Actions workflow.

Here are some of the most common options you can use when defining steps in a workflow:

**`uses`**: Specifies an action to run as part of the step.

```yaml
- uses: actions/checkout@v2
```

**`run`**: Specifies a command to run as part of the step.

```yaml
- run: echo "Hello, world!"
```

**`with`**: Provides input parameters for the action specified in `uses`.

```yaml
- uses: actions/setup-node@v2
  with:
  node-version: '14'
```

**`env`**: Sets environment variables for the step.

```yaml
- run: echo "Hello, world!"
  env:
  MY_VAR: "value"
```

**`if`**: Adds a conditional statement to determine whether the step should run.

```yaml
- run: echo "This runs only on main branch"
  if: github.ref == 'refs/heads/main'
```

**`continue-on-error`**: Specifies whether to continue running subsequent steps if this step fails.

```yaml
- run: some-command
  continue-on-error: true
```

**`timeout-minutes`**: Sets a timeout for the step.

```yaml
- run: long-running-command
  timeout-minutes: 10
```

**`id`**: Sets an identifier for the step, which can be used to reference the step's outputs in later steps.

```yaml
- id: step_id
  run: echo "Hello, world!"
```

**`working-directory`**: Specifies the working directory for the step.

```yaml
- run: echo "Hello, world!"
  working-directory: ./path/to/dir
```

## Conclusion

GitHub Actions is a powerful tool that allows you to automate your software development workflows. By defining workflows in YAML files, you can create custom automation processes that build, test, and deploy your code. Understanding the key concepts and options available in GitHub Actions will help you create efficient and effective workflows for your projects. For more information, check out the [GitHub Actions documentation](https://docs.github.com/en/actions).
