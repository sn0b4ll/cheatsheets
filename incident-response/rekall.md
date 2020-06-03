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

# Advanced Stuff
## Find Prog owning specific memory adress / find virtual addr from physical addr
In Rekall: `ptov(<adress>)`

Where `ptov` stands for physical to virtual
