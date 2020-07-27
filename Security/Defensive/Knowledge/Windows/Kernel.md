# Structures
| Struc  | Desc |
| ------------- | ------------- |
| \_KDDEBUGGER_DATA64 | KDBR-Structure, can be used for example to determine windows version |
| \_LIST_ENTRY | Structure for an simple List-Entry |
| \_EPROCESS | Structure of the EPROCESS-Block, can be used against an process-addr |
| \_LDR_DATA_TABLE_ENTRY | Module-Entry from the LDR-Table. Can be used against modules as seen by modules() |

# Pool
Get an overview of pools and pooltags.

| Pool-Tag  | Desc |
| ------------- | ------------- |
| Proc  | Number of Processes  |
| Key | Number of reg-keys |
| File | Number of File-Objects |
| Thre | Number of Threads |
| Driv | Number of Drivers |
| MnLd | Number of Modules |
| Muta | Number of Mutants |
| UdpA | UDP-Network-Listener (UDP_ENDPOINT) |
| TcpL | TCP-Network-Listener (TCP_LISTENER) |
| TcpE | TCP-Connection (TCP_ENDPOINT) |

More in pooltag.txt in WDK. or https://docs.microsoft.com/en-us/archive/blogs/yongrhee/pool-tag-list

Data can be pulled by pools and pool_tracker in rekall.
TODO How to get this in vol.

