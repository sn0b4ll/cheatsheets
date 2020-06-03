# Basic Usage
`vol.py -f <image> --profile=<profile> [plugin|volshell]`

## List all plugins ans profiles
--info

## Find the right profile
imageinfo

# Usefull Plugins
## psscan
Carves the image for processes.

## pslist
Follows the EProcess-List for processes (fast, but may miss unlinked/dead processes).

`vol.py -f <image> --profile=<profile> pslist`

## pstree
Show processes in tree-view.

`vol.py -f <image> --profile=<profile> pstree`

## psxview
Use different techs to detect processes and compare them to find "hidden" processes. `-P` gives the physical address for for example procdump, `-R` filters out known processes.

`vol.py -f <image> --profile=<profile> psxview [-P]`

## procdump
Dump a proc by offset.

`vol.py -f <image> --profile=<profile> procdump -o <offset> -D <output-dir>`

## cmdscan
## strings
## modules and moddump
Use 

`vol.py -f <image> --profile=<profile> modules`

to list all loaded modules from the LDRT (LoadeR Data Table?) and

`vol.py -f <image> --profile=<profile> moddump -b <base_addr> -D <out_dir>`

to dump it.

## ssdt
SystemServiceDescriptorTable

Tipp for easily finding rouge drivers:

`vol.py -f <image> --profile=<profile> ssdt | egrep -v "ntosk|win32"`

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
| db(\<addr\>) | Show data (hex and ascii) at addr |
| cc(pid=<pid>) | Switch context to other process |
| dt("\<Type\>") | Display Type Structure (see Structures below)  |
| dt("\<Type\>", <addr>) | Populate structure with data at addr |
| modules() | List all modules loaded in the image. |
| ps() | Show processes |
| dis(<addr>) | Show dissasembly for addr |
| self._proc.get_process_address_space().read(\<addr\>, \<size\>) | Return the process data for \<addr\> with length \<size\>. |
  
Additionally normal python-code (like open, loops etc.) will run, since it's an iPython-Shell (to my knowledge).
  
  ## Structures
| Struc  | Desc |
| ------------- | ------------- |
| \_KDDEBUGGER_DATA64 | KDBR-Structure, can be used for example to determine windows version |
| \_LIST_ENTRY | Structure for an simple List-Entry |
| \_EPROCESS | Structure of the EPROCESS-Block, can be used against an process-addr |
| \_LDR_DATA_TABLE_ENTRY | Module-Entry from the LDR-Table. Can be used against modules as seen by modules() |

## How-To on dumping things via volshell

1. Identify target context (`ps`, `modules`, etc.)
2. Switch to context (`cc`)
3. Identify base-addr of wanted object (`handles`, `modules`)
4. Identify size of wanted object (`dt` + right structure)
5. Use `self._proc.get_process_address_space().read(\<addr\>, \<size\>)` to get data and write it to file via python normal file interaction (`open`).

# Possible TODOs
- Enhance pslist to match the one from recall (also look at CSRSS, Handles, Sessions, PspCidTable, not "only" PsActiveProcessHead)
- ptov in vol
