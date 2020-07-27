# Volshell
## Params
| Command  | Desc |
| ------------- | ------------- |
| `-p <pid>` | Start in the context of process defined by the pid |


## Commands
| Command  | Desc |
| ------------- | ------------- |
| hh() | Basic help |
| sc() | Show context for virtual address space |
| db(\<addr\>) | Show data (hex and ascii) at addr |
| cc(pid=<pid>) | Switch context to other process |
| dt("\<Type\>") | Display Type Structure (see [Windows-Kernel](Windows-Kernel))  |
| dt("\<Type\>", <addr>) | Populate structure with data at addr |
| modules() | List all modules loaded in the image. |
| ps() | Show processes |
| dis(<addr>) | Show dissasembly for addr |
| self._proc.get_process_address_space().read(\<addr\>, \<size\>) | Return the process data for \<addr\> with length \<size\>. |
  
Additionally normal python-code (like open, loops etc.) will run, since it's an iPython-Shell (to my knowledge).
 

## How-To on dumping things via volshell

1. Identify target context (`ps`, `modules`, etc.)
2. Switch to context (`cc`)
3. Identify base-addr of wanted object (`handles`, `modules`)
4. Identify size of wanted object (`dt` + right structure)
5. Use `self._proc.get_process_address_space().read(\<addr\>, \<size\>)` to get data and write it to file via python normal file interaction (`open`).