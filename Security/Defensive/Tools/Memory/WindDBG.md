# Metdata

# Description

# Usage

## Commands
| Pool-Tag  | Desc |
| ------------- | ------------- |
| `dd <addr>` | Show Dwords at addr |
| `db <addr>` | Show Bytes at addr |
| `dt nt!\_<struc>` | Show info on structure (see [Windows-Kernel](Windows-Kernel)) |
| `dt [-b] nt!\_<struc> <addr>` | Populate structure with data from addr. `-b` walks the structure recursively. |
| `s <start_addr> [end_addr\|length] <term>` | Search in memory regions. `<term>` can be as simple as `4d 5a`for MZ. |
| `x nt!<string>` | Show symbol names for string-filter |
| `!process 0 0` | As pslist. The second 0 can be increased for deeper scanning (threats etc.) |
| `!process <addr>` | Shows detailed infos on process at addr. |
| `!dml_proc [<addr>]` | Also a pslist, more readable but less info. If addr is given, shows more details on the single process. |
| `.process /p /r <addr>` | Change to the context of process at addr. (eq to cc in volshell) |
| `lm f` | List modules |
| `!handle` | Shows open handles, takes params (please see doc).
| `!peb [<addr>]` | Show peb of current context or from addr if given. |
| `!vad [<addr>] [1]` | Show the vads for current or other process if addr is given. The 1 at the end can be used to make the command verbose. |
| `!address -map` | Show address/pool-ranges. |
| `.writemem <destination> <start> <end>` | Writes a portion of the ram to disk.|