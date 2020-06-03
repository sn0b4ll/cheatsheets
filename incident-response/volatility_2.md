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
## yarascan
[Doku](https://github.com/volatilityfoundation/volatility/wiki/Command-Reference-Mal#yarascan)
### Params

| Param  | Desc |
| ------------- | ------------- |
| `--yara-file=<path>`  | Path to Yara-File  |
| `--yara-rules=<rule>`  | Run specific rule given as string  |
| `-K`  | Also search in Kernel-Mem  |
| `-Y <rule>`  | Like `--yara-rules` |
| `-Y <path>`  | Like `--yara-file` |

### Examples
Default:
python vol.py -f zeus.vmem yarascan --yara-file=/path/to/rules.yar

Search for String, also include Kernel-Mem:

`vol.py -f <image> --profile=<profile> yarascan -K -Y "string"`
