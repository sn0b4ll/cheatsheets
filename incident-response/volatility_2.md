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
