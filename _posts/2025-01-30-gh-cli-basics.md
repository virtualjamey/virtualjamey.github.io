---
title: GitHub CLI Basics
description: Basics of the GitHub CLI
date: 2025-01-30 14:40:00 -0300
# image:
#   path: "/assets/img/posts/wall.png"
#   alt: "Breaking Through The Wall"
category:
 - github
 - git
 - cli
 - fundamentals
tags:
  - github
  - git
  - cli
  - fundamentals
---

### What is GitHub CLI?

Github CLI is a command-line interface for GitHub that allows you to interact with GitHub repositories, issues, pull requests, and more directly from the command line. It provides a convenient way to perform common GitHub operations without leaving the terminal.

#### GitHub CLI Installation

You can install Github CLI by downloading the binary from the [GitHub CLI releases page](https://github.com/cli/cli/releases) and adding it to your system's PATH. Alternatively, you can use a package manager like Homebrew on macOS or Chocolatey on Windows to install Github CLI.

#### GitHub CLI Configuration

After installing Github CLI, you need to authenticate with your GitHub account using the `gh auth login` command. This will open a browser window where you can authorize the CLI to access your GitHub account. Once authenticated, you can start using Github CLI to interact with GitHub repositories.

<image src="assets/img/posts/ghcliauth.gif" alt="Spinners" width="450" /> 

#### GitHub CLI Commands

Github CLI provides a set of commands for working with GitHub repositories, issues, pull requests, and more. Some of my most used commands are:

##### Repositories

- `gh repo list`: List GitHub repositories.
- `gh status`: Show the status of the current repository.
- `gh repo view <repository>`: View a GitHub repository in the browser.
- `gh repo create <repository-name>`: Create a new GitHub repository.
- `gh repo clone <repository>`: Clone a GitHub repository to your local machine.
- `gh repo fork <repository>`: Fork a GitHub repository.

##### Pull Requests

- `gh pr list`: List pull requests in a GitHub repository.
- `gh pr status`: Show the status of pull requests in the current repository.
- `gh pr view <pull-request-number>`: View a pull request in the browser.
- `gh pr create`: Create a pull request on GitHub.
- `gh pr checkout <pull-request-number>`: Check out a pull request locally.
- `gh pr merge <pull-request-number>`: Merge a pull request.

##### Issues

- `gh issue list`: List issues in a GitHub repository.
- `gh issue status`: Show the status of issues in the current repository.
- `gh issue view <issue-number>`: View an issue in the browser.
- `gh issue create`: Create a new issue on GitHub.

There are many more commands available in Github CLI, and you can explore them by running `gh help` or `gh help <command>`. or by visiting the [GitHub CLI documentation](https://cli.github.com/manual/).

#### GitHub CLI Tips

- Use `gh help` to get help on commands and flags.
- Use `gh alias set` to create custom aliases for frequently used commands.
- Use `gh config set` to configure default settings for the CLI.

GitHub CLI supports tab completion by running `gh completion` and using the output in your shells runtime configuration.
{: .bubble-note}

#### Conclusion

GitHub CLI is my favorite way to interact with GitHub repositories and perform common GitHub operations from the command line.