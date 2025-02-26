---
title: CyberArk Vault DBParm.ini Configuration File
description: Summary of CyberArk Vault DBParm.ini configuration file.
date: 2025-02-14 14:40:00 -0300
# image:
#   path: "/assets/img/posts/wall.png"
#   alt: "Breaking Through The Wall"
# category:
#  - cyberark
#  - PAM
#  - logs
#  - Privileged Access Management
#  - fundamentals
#  - vault
tags:
  - cyberark
  - PAM
  - config
  - privileged_access_management
  - fundamentals
  - vault
---

## Introduction

The `DBParm.ini` file is a core configuration file for the CyberArk Vault. It contains essential parameters for the Vault's operation, including database settings, paths to key files, and other critical configuration options. The `DBParm.ini` file is located in the `C:\Program Files (x86)\PrivateArk\Server\Conf` directory by default. These are some of the most important parameters in the `DBParm.ini`
<br>

| **Parameter** | **Description** |
|---------------|-----------------|
| `AutoClearSafeHistory` | Configures automatic clearing of Safe history. Acceptable values include enabling/disabling, setting intervals in hours or days, and specifying time ranges. Default is `Yes,1,1,2`. |
| `AutoClearUserHistory` | Manages automatic clearing of user history with options for enabling/disabling, interval settings, and time frames. Default is `Yes,1,3,4`. |
| `ClearSafeHistoryChunkSize` | Defines the number of Safe history records to clear in a single operation. Default is `200,000`. |
| `ObjectsPerSafeWarningThreshold` | Sets the maximum recommended number of objects in a Safe before a warning is logged. Default is `300,000`. |
| `DaysForAutoClear` | Specifies the interval in days between automatic clearing of Safe and user log messages. Default is `30`. |
| `EmergencyStationIP` | Designates the IP address of the emergency station. Default is `None`. |
| `EnablePreDefinedUsers` | Determines which predefined users can log on or appear in user lists. Options include `All`, `None`, `Auditor`, `Operator`, or combinations thereof. Default is `All`. |
| `FreeDiskSpaceWarningThreshold` | Triggers a warning when the Safes directory has less than the specified free space in MB. Default is `100`. |
| `GetFileBufferSize` | Sets the buffer size in bytes for caching during file retrieval operations. Default is `2,000,000`. |
| `GroupMergeAlgorithm` | Defines how the Vault unifies group permissions. Options are `DenyOverrides` or `FirstApplicable`. Default is `DenyOverrides`. |
| `LogRetention` | Specifies the number of days to retain records in `ITALOG.log`. Default is `7`. |
| `MaxStagingAreaPutSize` | Limits the number of files that can be placed in the Staging Area. A value of `0` indicates no limit. Default is `0`. |
| `MaxAccessViolations` | Sets the number of allowed access violations in the 'All' network area before suspending a user. Default is `5`. |
| `UserLockoutPeriodInMinutes` | Defines the duration in minutes for which a user is locked out after exceeding allowed access violations. Default is `30`. |
| `MinSupportedClientVersion` | Specifies the minimum client version permitted to connect to the Vault. Format: `x.x.x.x`. Default for a clean Vault is `11.5.0.0`; for an upgraded Vault, there is no default. |
| `PreDefinedGroupsOwnerRemoval` | Indicates which predefined groups can be removed from Safes. Options include `All`, `None`, `Auditors`, `Operators`, or combinations thereof. Default is `All`. |
| `ParallelTasks` | Determines the number of parallel transactions the server can perform, with an optional second number for lightweight transactions. Default is `20,1`. |
| `AllowedVirusSafeFileTypes` | Lists file types accepted in a virus-free Safe. Default is `TXT`. |
| `VirusSafeFileSuffixes` | Specifies additional file suffixes considered acceptable in a virus-free Safe. Default is `None`. |
| `PerfFilterEvents` | Identifies event codes to monitor for performance tracking. Default is `None`. |
| `PerfFilterTransactions` | Specifies transactions to monitor for performance analysis. Default is `None`. |
| `PerfFilterUsers` | Lists users to monitor for performance purposes. Default is `None`. |
| `DatabaseConnectionPasswordFile` | Indicates the file containing the encrypted password for database access. Default is `VaultUser.pass` in the Vault keys directory. |
| `DatabaseReplicationPasswordFile` | Specifies the location of the MySQL replication user's password file. Default is `ReplicationUser.pass` in the same directory as the `DatabaseConnectionPasswordFile`. |
| `BackupFilesDeletion` | Points to the location of MySQL binary logs used for incremental backups and disaster recovery. Default is `%MetadataDir%\mysql-bin.*`. |
| `BackupKey` | Provides the full path to the backup key file. Default is `None`. |
| `VaultEventNotifications` | Determines which Vault event notifications are written. Options include `NotifyOnNewRequest`, `NotifyOnConfirmRequest`, `NotifyOnRejectRequest`, and `NotifyOnDeleteRequest`. Default is `None`. |
| `SyslogServerIP` | Specifies the IP address(es) or hostname(s) of Syslog servers to receive messages. Multiple values are separated by commas. Default is `None`. |
| `SyslogServerPort` | Defines the port(s) used to connect to Syslog servers. Multiple values are separated by commas. Default is `514`. |
| `SyslogServerProtocol` | Sets the protocol(s) for sending audit logs via Syslog. Options are `TCP`, `UDP`, or `TLS`. Multiple values are separated by commas. Default is `UDP`. |
| `SyslogTrustedCAPath` | Indicates the path to the root CA certificate that signed the Syslog server certificate. Default is `None`. |
| `SyslogMessageCodeFilter` | Specifies which message codes are sent from the Vault to the SIEM application via Syslog. Multiple values are separated by commas. Default is `None`. [More info here](https://docs.cyberark.com/pam-self-hosted/latest/en/content/pasref/vault%20audit%20action%20codes.htm?Highlight=Vault%20Audit%20Action%20Codes) |
| `SyslogTranslatorFile` | Points to the XSL file used to parse CyberArk audit records into the Syslog protocol. Default is `None`. |
| `UseLegacySyslogFormat` | Controls whether Syslog messages are sent in the newer format (RFC 5424) or a legacy format. Default is `No`. |
| `SyslogProcessingMessagesLimit` | Sets the maximum number of messages the Syslog processing queue can hold before issuing a warning. Default is `10,000`. |
| `SyslogServerMessagesLimit` | Defines the maximum number of messages awaiting acknowledgment from the Syslog server before issuing a warning. Default is `1,000`. |
| `SyslogQueueFullWarningInterval` | Specifies how frequently (in seconds) "message queue full" warnings are displayed in the Server Console. Default is `900` (15 minutes). |
| `DedicatedTasksAllocation` | Allocates a specific number of concurrent Vault transactions to designated interface IDs. Default is `None`. |
| `LockTimeout` | Sets the timeout in minutes after which users must re-authenticate to the Vault. Default is `30`. |
| `TerminateOnDBErrorCodes` | Lists database error codes that will cause the Vault to shut down if encountered. Default includes `2003` (indicating the MySQL client lost connection to the Vault). |
| `PimsuPoliciesManager` | Names the group authorized to define and manage OPM commands at the platform level. Default is `Vault Admins`. |
| `MonitorFWRulesInterval` | Determines the frequency (in minutes) that the Vault checks for unauthorized firewall rule changes. Default is `15`. |
| `MonitorLongTransactions` | Sets the interval (in minutes) between checks for long-running component activities. Default is `1`. |
| `MonitorLongTransactionsThreshold` | Specifies the duration (in minutes) that a component activity must exceed to be considered long-running. Default is `5`. |
| `MonitorLongTransactionsAction` | Defines the action taken when a long-running component activity is detected. Options include `Log`, `LogAndNotify`, and `LogAndTerminate`. Default is `Log`. |
| `MonitorLongTransactionsNotification` | Specifies the email addresses to notify when a long-running component activity is detected. Default is `None`. |

For more information on the `DBParm.ini` file and its parameters, [refer to the CyberArk documentation.](https://docs.cyberark.com/pam-self-hosted/latest/en/content/pasref/dbparm.ini.htm)