# Basic Usage

## Cache and Config
Config is in `.rekallrc`. A cache can be defined there, so rekall does not rerun thinks it already did in the past.

## Read from File:
`rekall[.exe] -f <file>`

## Live Analysis
Windows:
`rekall.exe live`

Linux:
`rekall --live`

## List plugins
In Rekall:
`plugins.<tab><tab>` or `dir(plugins)`

## Help on plugin
`<pluginname>?`

## Context-Related Commands
`cc <pid>` change to pids context

# Advanced Stuff / Usefull Plugins
## Find Prog owning specific memory adress / find virtual addr from physical addr
### ptov
In Rekall: `ptov(<adress>)`

Where `ptov` stands for physical to virtual

### pastovas
In Rekall: `pas2vas offsets="<address>"`

### YaraScan
See help for params (too many).

Still some examples:
- `yarascan(yara_file="<location of yara rule>")`
- `yarascan(string="<string>",scan_kernel="True"`

### pslist
Does what you think it does :)

### dlllist
`dlllist <pid>`

### peinfo

### users
Shows current users from SAM-Reg-Hive.

### pools and pool_tracker
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

More in pooltag.txt in WDK. or https://docs.microsoft.com/en-us/archive/blogs/yongrhee/pool-tag-list
