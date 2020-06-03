# Basic Usage
`vol.py -f <image> --profile=<profile> [plugin|volshell]`

## List all plugins ans profiles
--info

## Find the right profile
imageinfo

# usefull plugins
## psscan
## pslist
## cmdscan
## strings
## modules
List all loaded modules from the LDRT (LoadeR Data Table?).

## printkey
`vol.py -f <image> --profile=<profile> printkey -K "<searchterm>"`

where searchterm should be something like "Microsoft\Windows NT\CurrentVersion" ans should not include the hive name.

## yarascan
[Doku](https://github.com/volatilityfoundation/volatility/wiki/Command-Reference-Mal#yarascan)
### Params

| Param  | Desc |
| ------------- | ------------- |
| `--yara-file=<path>`  | Path to Yara-File  |
| `--yara-rules=<rule>`  | Run specific rule given as string  |
| `-K`  | Search in Kernel-Mem |
| `-A`  | Sarch in Kernel- and User-Mem |
| `-p <pids>`  | Work on those pids (comma-separated list) |
| `-Y <rule>`  | Like `--yara-rules` |
| `-Y <path>`  | Like `--yara-file` |

More Params via `vol.py yarascan -h`

### Examples
Default:
`vol.py -f <image> yarascan --yara-file=</path/to/rules.yar>`

Search for String, also include Kernel-Mem:

`vol.py -f <image> --profile=<profile> yarascan -K -Y "string"`

## kdbgscan
Usefull if imageinfo fails and if one wants to know the offset to the KDBG in an image.

# Volshell-Commands
| Command  | Desc |
| ------------- | ------------- |
| hh() | Basic help |
| sc() | Show context for virtual address space |
| cc(pid=<pid>) | Switch context to other process |
| dt("\<Type\>") | Display Type Structure (see Structures below)  |
| dt("\<Type\>", <addr>) | Populate structure with data at addr |
| modules() | List all modules loaded in the image. |
| ps() | Show processes |
  
  ## Structures
| Struc  | Desc |
| ------------- | ------------- |
| "\_KDDEBUGGER_DATA64" | KDBR-Structure |
| "\_LIST_ENTRY" | Structure for an simple List-Entry |
| "\_EPROCESS" | Structure of the EPROCESS-Block |
| "\_LDR_DATA_TABLE_ENTRY" | Module-Entry from the LDR-Table |
