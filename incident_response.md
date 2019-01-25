# Incident / Compromise Response Cheatsheet
Version: 1.1

## Log-Analysis
### Basic Event-IDs
#### Login and Access Activity
| Event-ID | Description | Where |
| --- | --- | --- | 
| 4624 | Logon successful| Destination System |
| 4625 | Logon failed | Destination System |
| 4634/4647 | Logoff | Destination System |
| 4648 | Logon with explicit credentials (for example runas) | Originating or Both Systems |
| 4672 | Logon with Admin-Rights | Destination System |
| 4768 | Ticket Granting Ticket was granted | Authenticating System |
| 4769 | Service Ticket requested | Authenticating System |
| 4771 | Kerberos pre-authentication failed | Authenticating System |
| 4776 | The domain controller attempted to validate the credentials for an account |  Authenticating System |
| 4778 | RDP Session connected / reconnected | Destination System |
| 4779 | RDP Session disconnected | Destination System |
| 5140 | Network Share was accessed | Destination System |
| 5145 | Shared Object accessed (needs to be enabled by policy) | Destination System |

##### Logon-Types
| Logon-Type | Name | Description |
| --- | --- | --- |
| 2 | Interactive | A user logged on to this computer. |
| 3 | Network | A user or computer logged on to this computer from the network. |
| 4 | Batch | Batch logon type is used by batch servers, where processes may be executing on behalf of a user without their direct intervention. |
| 5 | Service | A service was started by the Service Control Manager. |
| 7 | Unlock | This workstation was unlocked. |
| 8 | Network Cleartext | A user logged on to this computer from the network. The user's password was passed to the authentication package in its unhashed form. The built-in authentication packages all hash credentials before sending them across the network. The credentials do not traverse the network in plaintext (also called cleartext). |
| 9 | New Credentials | A caller cloned its current token and specified new credentials for outbound connections. The new logon session has the same local identity, but uses different credentials for other network connections. (runas) |
| 10 | Remote Interactive | A user logged on to this computer remotely using Terminal Services or Remote Desktop. |
| 11 | Cached Interactive | A user logged on to this computer with network credentials that were stored locally on the computer. The domain controller was not contacted to verify the credentials. |
| 12 | Cached Remote Interactive | Same as 10 |
| 13 | Cached Unlock | Same as 7 |

##### Failed Logon-Types
| 4471| 4776/4625 | Description |
| --- | --- | --- |
| 0x6 | 0xC0000064 | Invalid Username |
| 0x7 | - | Requested Server not found |
| 0xC | 0xC0000070 | Policy restriction prohibited logon |
| 0x12 | 0xC0000234 | Account logged, disabled or expired |
| 0x17 | 0xC0000071 | Password expired |
| 0x18 | 0xC000006A | Password invalid |
| 0x25 | - | Time between machines out of sync |


https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2003/cc787567(v=ws.10)

#### User and Group Management
| Event-ID | Description |
| --- | --- |
| 4720 | Account was created |
| 4722 | Account was enabled |
| 4724 | Password-Reset-Attempt |
| 4728 | A User was added to a security-enabled global group |
| 4732 | A User was added to a security-enabled local group |
| 4735 | A security-enabled local group was changed |
| 4738 | A user account was changed |
| 4756 | A member was added to a security-enabled universal group |

#### Log-Clearing
| Event-ID | Description |
| --- | --- |
| 1102 | Audit log cleared (Security Log) |
| 104 | Audit log cleared (System Log) |

#### Service-related Events
##### Security-Log
| Event-ID | Description |
| --- | --- |
| 4697 | Service installed (needs to be enabled by policy)|
| 4698 | Scheduled Task created |
| 4702 | Scheduled Task update |
| 4699 | Scheduled Task deleted |
| 4700 | Scheduled Task enabled |
| 4701 | Scheduled Task disabled |

##### System-Log
| Event-ID | Description |
| --- | --- |
| 7034 | Services crashed |
| 7035 | Service send start/stop |
| 7036 | Service started/stoped |
| 7040 | Service start type changed |
| 7045 | Service installed |

#### Application-related Events
##### Meta
Only logged when application uses windows installer api and all Events are stored in the application log.

##### Events
| Event-ID | Description |
| --- | --- |
| 1033 | Installation completed |
| 1034 | Removal completed |
| 11707 | Installation completed success |
| 11708 | Installation operation failed |
| 11724 | Application removal successful |

#### Process-related Events
##### Meta
Needs to be enabled by policy.

##### Events
| Event-ID | Description |
| --- | --- |
| 4688 | Process created or exited |

#### Powershell-related Events
##### Meta
Needs to be enabled by policy.

##### Events
| Event-ID | Description |
| --- | --- |
| 4104 | Includes the Script itself |
| 4105 | Script started |
| 4106 | Script stop |

#### WMI-related Events
##### Meta
Enabled in W10 / Win2012R2+ by default. Log ist WMI-Activity/Operational

##### Events
| Event-ID | Description |
| --- | --- |
| 5859 | Details for created filter |
| 5861 | Record filter created |


### Combined Events
| Indicators | Description |
| --- | --- |
| 4624 + 4672 | Privileged Logon |
| (4624\|4625) + Logon-Type 2 + PsExec | PsExec with explicit credentials |

### SIDs
| SID | Description |
| --- | --- |
| S-1-5-21domain-500 | Built-in Administrator accounts in their respective issuing authorities |
| S-1-5-21domain-512 | Domain Admin |
| S-1-5-21domain-513 | Domain User |
| S-1-5-32-544 |
| S-1-5-21domain-1... | Local Users (1000 often used as normal user with Admin-Rights) |

Source: https://support.microsoft.com/sv-se/help/243330/well-known-security-identifiers-in-windows-operating-systems
