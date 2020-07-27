# Basic Usage
`vol.py -f <image> --profile=<profile> [plugin|volshell]`

## List all plugins ans profiles
--info

## Set custom plugin path
Use `--plugins`-Switch. This _has_ to be the first param to vol!

`vol.py --plugins=<dir> [...]`

## Find the right profile
imageinfo

## Convert images
imagecopy

# Usefull Plugins

## Processes
### psscan
Carves the image for processes.

### pslist
Follows the EProcess-List for processes (fast, but may miss unlinked/dead processes).

`vol.py -f <image> --profile=<profile> pslist`

### pstree
Show processes in tree-view, relies on pslist and won't show other processes then pslist. `-v` shows alot more information like cmd-line, path and base-address.

`vol.py -f <image> --profile=<profile> pstree [-v]`

### psxview
Use different techs to detect processes and compare them to find "hidden" processes. `-P` gives the physical address for for example procdump, `-R` applies "Okay" to known "False"-Entries.

`vol.py -f <image> --profile=<profile> psxview [-P]`

### procdump
Dump a proc by offset.

`vol.py -f <image> --profile=<profile> procdump -o <offset> -D <output-dir>`

### dlllist (32bit)
Relies on pslist and lists all loaded DLLs. Only works with 32bit-Processes!

### ldrmodules (64bit)
List DLLs for 64bit-Process.

### dlldump
`[..] dlldump -p <pid> -r <regex_for_name> -i -D <output_dir>`

## verinfo
## enumfunc
List imports/exports of an dll

## handles
Show handles, try to filter for PID (`-p`), Types (`-t`0) or other things or it will be noisy! You can also use `-s` to further suppress "empty" entries.

## modules/modscan and moddump
Use 

`vol.py -f <image> --profile=<profile> modules`

to list all loaded modules from the LDRT (LoadeR Data Table?) and

`vol.py -f <image> --profile=<profile> moddump -b <base_addr> -D <out_dir>`

to dump it.
## Services
### svcscan
Reports back services from the image incl. Service State.

## Network
### ndispktscan
Vista+, carves for network packages, can save as pcap. Takes longer then bulk_extractor, but produces same results.

`[..] ndispktscan -p <out.pcap>`

### netscan
Works on Vista and later. Use `-V` if you want to get the virtual addresses.

## registry
Please see specific [[Registry]].

## Drivers

### devicetree
Might show evil drivers if they register as/ listen to devices.

### driverscan

### driverirp

### Unloadedmodules

## Hooking / Memory-Injection / Rootkits
### malfind
`vol.py -f <image> --profile=<profile> malfind [-p <pid>]`

Scrap for execute/rw-pages with code. [Doc](https://github.com/volatilityfoundation/volatility/wiki/Command-Reference-Mal#malfind).


### apihooks
`vol.py -f <image> --profile=<profile> apihooks [-p <pid>]`

Lookt at the IAT and EAT of processes and if all thinks there point at "valid" locations. Takes long, consider using quick-mode. See [Doc](https://github.com/volatilityfoundation/volatility/wiki/Command-Reference-Mal#apihooks).

## Other

### cmdscan

### filescan and dumpfiles
Scan for files in memory and use `[...] dumpfiles -Q <physical_addr> -n -D <out_dir>` to dump it.

### hashdump
Dump the windows paswort hashes.

### cachedump
Dump cached domain credentials.

### strings
### mutantscan
### thrdscan
### mbrparser
### shutdowntime
### systeminfo
### envars
### callbacks
`vol.py -f <image> --profile=<profile> callbacks [-V]`

Scans for kernel callbacks. `-V` does only show active callbacks in virtual memory.

### memmap
### memdump
### dumpwmem
Dump only heap-memory (including most of the user activity).

### impscan
### autitpol
shellbags
### clipboard
`vol.py -f <image> --profile=<profile> clipboard -v`

TODO: Update for Win10

### wndscan
Gives user statistics (like is it interactive?).

`vol.py -f <image> --profile=<profile> wndscan`

### screenshot
Abstract screenshot from GDI.

`vol.py -f <image> --profile=<profile> screenshot -D <dump_dir>`

### shimcachemem
`vol.py -f <image> --profile=<profile> shimcachemem`

shimcachemem pulls from MEMORY, while the normal shimcache-plugin is file-based and would need a restart before detecting files.

### prefetchparser
`vol.py -f <image> --profile=<profile> prefetchparser`

### atoms
Very rarely one can find atoms from atom-bombing code-injection still in the memory.

### ssdt
SystemServiceDescriptorTable

Tipp for easily finding rouge drivers:

`vol.py -f <image> --profile=<profile> ssdt | egrep -v "ntosk|win32"`

### yarascan
[Doku](https://github.com/volatilityfoundation/volatility/wiki/Command-Reference-Mal#yarascan)
#### Params

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

#### Examples
Default:
`vol.py -f <image> yarascan --yara-file=</path/to/rules.yar>`

Search for String, also include Kernel-Mem:

`vol.py -f <image> --profile=<profile> yarascan -K -Y "string"`

### messagehooks
Looks for message hooks, sometimes used by walware injecting itself via `SetWindowsHookEx` into other processes.

### kdbgscan
Usefull if imageinfo fails and if one wants to know the offset to the KDBG in an image.

# Possible TODOs
- [ ] Enhance pslist to match the one from recall (also look at CSRSS, Handles, Sessions, PspCidTable, not "only" PsActiveProcessHead)
- [ ] ptov in vol
