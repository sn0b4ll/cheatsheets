# Meta
#filesystem #forensic #volatility2 #vol2 #volatility

[[Volatility 2]] plugins in order to review infos on the file-system from memory.

# Plugins
| Plugin| Desc |
| ------------- | ------------- |
| mftparser | `[..] mftparser --output=body --output-file=<outfile>`, can be converted with mactime to csv.|
| usnparser | `[..] unsparser -CS` generates Comma-Separated list.|
| indx | Extract $I30-Entries. |
| logfile | Parse existing log files |
| timeliner | Runs differen plugins, for body-format: `[..] timeline --output=body --output-file=<outfile>`|
