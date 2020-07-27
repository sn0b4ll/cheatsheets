# Metadata
Project: https://github.com/google/rekall

**Rekall is considered "dead" by author! See [here](https://github.com/google/rekall/issues/518#issuecomment-570610707).** Therefore it might not work with current memory images, but should work finde with older ones.

# Usage
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
