# Get Registry Hive
Either via harddrive (but there might be some keys not yet written to disk) or of the RAM, see [[Security/Defensive/Tools/Memory/Volatility 2/Registry]]

# Extracting values from the hive
## rip.pl
rip.pl allows to convert a registry-hive (.reg) to a .txt-File for simpler parsing:

`rip.pl -r <reg-file> -f <hivename> > <out_file>`