---
title: Linux Users and Groups Part Two
description: More basics of Linux users and groups
date: 2025-02-01 16:40:00 -0300
# image:
#   path: "/assets/img/posts/wall.png"
#   alt: "Breaking Through The Wall"
category:
 - linux
 - users
 - groups
 - passwd
 - fundamentals
tags:
  - linux
  - users
  - groups
  - fundamentals
---

### Introduction to Linux Users and Groups Part 2

Following from [Part One](https://jamey.one/linux-users-and-groups-part-1) this article provides an overview of Linux user and group management commands.

#### Core User and Group Management Commands

- **whoami**: Display the username of the current user.
- **users**, **who** and **w**: Display currently logged-in users.
- **id**: Display user and group information.
- **groups**: Display group membership information.
- **su**: Switch user.

To display the username of the current user, you can use the `whoami` command:

```bash
whoami
```

To display currently logged-in users, you can use the `w`, `who`, or `users` command:

```bash
w
who
users
```

These commands fundamentally do the same thing and differ by their options and the formatting of their output.
{: .bubble-note}

To display user and group information, you can use the `id` command:

```bash
id
```

To display group membership information, you can use the `groups` command:

```bash
groups
```

To switch user, you can use the `su` command followed by the username:

```bash
su username
```

#### Sudo Command

The `sudo` command allows you to execute a command as another user, typically the root user. It is commonly used to perform administrative tasks that require elevated privileges instead of using the root account directly.

Sudo can be explained as "superuser do" or "substitute user do". It allows a permitted user to execute a command as the superuser or another user, as specified by the security policy. The security policy determines what users can run which commands on which machines and can be configured in the `/etc/sudoers` file.

#### Editing the Sudoers File

To add a user to the sudoers file, you can use the `visudo` command to edit the `/etc/sudoers` file. 

The `visudo` command should always be used to edit the sudoers file as it performs syntax checking to prevent errors.
{: .bubble-note}

#### The Sudoers File Syntax

The sudoers file uses a specific syntax to define user permissions. The following is an example of the sudoers file syntax:

```bash

# Clears environment variables by default
Defaults    env_reset

# Defines a secure path for executing commands
Defaults    secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"

# Root user can run any command on any host as any user or group
root    ALL=(ALL:ALL) ALL

# Members of the sudo group are granted sudo privileges
%sudo   ALL=(ALL:ALL) ALL

# Allow a specific user to run all commands as any user
username ALL=(ALL:ALL) ALL

# Allow a specific user to run a specific command as any user
username ALL=(ALL:ALL) /usr/bin/specific_command

# Allow a specific user to run all commands as a specific user
username ALL=(specific_user:ALL) ALL

# Allow a specific user to run all commands as any user without a password
username ALL=(ALL:ALL) NOPASSWD: ALL
```

Explanation of each part:

- `Defaults    env_reset`: Clears environment variables by default.
- `Defaults    secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"`: Defines a secure path for executing commands.
- `root    ALL=(ALL:ALL) ALL`: The root user can run any command on any host as any user or group.
- `%sudo   ALL=(ALL:ALL) ALL`: Members of the sudo group can run any command on any host as any user or group.
- `username ALL=(ALL:ALL) ALL`: The specified user can run any command on any host as any user or group.
- `username ALL=(ALL:ALL) /usr/bin/specific_command`: The specified user can run the specific command as any user or group.
- `username ALL=(specific_user:ALL) ALL`: The specified user can run any command as the specific user.
- `username ALL=(ALL:ALL) NOPASSWD: ALL`: The specified user can run any command as any user or group without being prompted for a password.









