---
title: Linux Users and Groups Part One
description: Basics of Linux users and groups
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

### Introduction

Linux is a multi-user operating system that allows multiple users to access the system simultaneously. 

Each user has a unique username and password, and belongs to one or more groups. This article provides an overview of Linux users and groups, including configuration files, user management, and group management.

#### Linux Users and Groups Configuration Files Overview

There are 6 main configuration files for linux users and groups:

1. **/etc/passwd** - Contains user information
2. **/etc/shadow** - Contains encrypted passwords
3. **/etc/group** - Contains group information
4. **/etc/gshadow** - Contains encrypted group passwords
5. **/etc/login.defs** - Contains login definitions
6. **/etc/default/useradd** - Contains default user information

#### /etc/passwd

The `/etc/passwd` file contains essential information about user accounts. Each line represents a user and has seven fields separated by colons (`:`):

1. **Username**: The user's login name.
2. **Password**: An `x` indicates that the password is stored in `/etc/shadow`.
3. **User ID (UID)**: A unique number assigned to each user.
4. **Group ID (GID)**: The primary group ID for the user.
5. **GECOS**: A comment field, often containing the user's full name.
6. **Home Directory**: The path to the user's home directory.
7. **Shell**: The user's default shell.

#### /etc/shadow

The `/etc/shadow` file stores encrypted user passwords and additional account information. Each line corresponds to a user in `/etc/passwd` and has nine fields:

1. **Username**: The user's login name.
2. **Encrypted Password**: The hashed password.
3. **Last Password Change**: The date of the last password change.
4. **Minimum Age**: The minimum number of days between password changes.
5. **Maximum Age**: The maximum number of days a password is valid.
6. **Warning Period**: The number of days before password expiration to warn the user.
7. **Inactive Period**: The number of days after password expiration before the account is disabled.
8. **Expiration Date**: The date when the account will be disabled.
9. **Reserved**: A reserved field for future use.

#### /etc/group

The `/etc/group` file defines groups on the system. Each line represents a group and has four fields:

1. **Group Name**: The name of the group.
2. **Password**: An `x` indicates that the password is stored in `/etc/gshadow`.
3. **Group ID (GID)**: A unique number assigned to each group.
4. **Group List**: A comma-separated list of users who are members of the group.

#### /etc/gshadow

The `/etc/gshadow` file stores encrypted group passwords and additional group information. Each line corresponds to a group in `/etc/group` and has four fields:

1. **Group Name**: The name of the group.
2. **Encrypted Password**: The hashed group password.
3. **Group Administrators**: A comma-separated list of group administrators.
4. **Group Members**: A comma-separated list of group members.

#### /etc/login.defs

The `/etc/login.defs` file contains configuration settings for user account creation and login behavior. Key settings include:

- **PASS_MAX_DAYS**: Maximum number of days a password is valid.
- **PASS_MIN_DAYS**: Minimum number of days between password changes.
- **PASS_WARN_AGE**: Number of days before password expiration to warn the user.
- **UID_MIN**: Minimum user ID for regular users.
- **UID_MAX**: Maximum user ID for regular users.
- **GID_MIN**: Minimum group ID for regular groups.
- **GID_MAX**: Maximum group ID for regular groups.

#### /etc/default/useradd

The `/etc/default/useradd` file contains default settings for new user accounts. Key settings include:

- **HOME**: The base directory for new user home directories.
- **INACTIVE**: The number of days after a password expires before the account is disabled.
- **EXPIRE**: The date when the account will be disabled.
- **SHELL**: The default shell for new users.
- **SKEL**: The directory containing default files for new user home directories.

#### Adding and Modifying Users and Groups

When a user is created, a corresponding group with the same name is usually created as well. The user's primary group is typically the group with the same name as the user. The users home directory is usually created in `/home/username` and is souced from the contents of `/etc/skel`.

To add a new user, you can use the `useradd` command followed by the username. For example:

```bash
sudo useradd newuser
```

To modify user properties, you can use the `usermod` command followed by the desired options. For example, to change a user's home directory:

```bash
sudo usermod -d /new/home/dir username
```

To add a new group, you can use the `groupadd` command followed by the group name. For example:

```bash
sudo groupadd newgroup
```

To modify group properties, you can use the `groupmod` command followed by the desired options. For example, to change a group's name:

```bash
sudo groupmod -n newgroup oldgroup
```

#### Deleting Users and Groups

To delete a user, you can use the `userdel` command followed by the username. For example:

```bash
sudo userdel olduser
```

To delete a group, you can use the `groupdel` command followed by the group name. For example:

```bash
sudo groupdel oldgroup
```

#### Managing User Passwords

To change a user's password, you can use the `passwd` command followed by the username. For example:

```bash
sudo passwd username
```

To lock or unlock a user account, you can use the `passwd` command with the `-l` or `-u` options. For example, to lock a user account:

```bash
sudo passwd -l username
```

To expire a user's password, you can use the `passwd` command with the `-e` option. For example:

```bash
sudo passwd -e username
```

#### Conclusion

This article provided an overview of Linux users and groups, including configuration files, user management, and group management. Understanding these concepts is essential for managing user accounts and permissions on a Linux system. In [Part Two](https://jamey.one/linux-users-and-groups-part-2), we explore user and group management commands in more detail.