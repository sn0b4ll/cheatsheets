# Basic Usage

## Read from File:
`rekall[.exe] -f <file>`

## Live Analysis
Windows:
`rekall.exe live`

Linux:
`rekall --live`

## List plugins
In Rekall:
`plugins.<tab><tab>`

## Help on plugin
`<pluginname>?`

# Advanced Stuff
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


