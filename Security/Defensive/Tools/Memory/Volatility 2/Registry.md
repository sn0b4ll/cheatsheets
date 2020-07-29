# Meta
Since there are so much [[Volatility 2]] -plugins for registry, I made an extra subpage.

# Plugins
## hivelist
`vol.py -f <image> --profile=<profile> hivelist`
Prints all registry hives found in the image.

## hivescan
`vol.py -f <image> --profile=<profile> hivescan`

## hivedump
`vol.py -f <image> --profile=<profile> hivedump -o <virtual_offest_of_hive>`

where the v-offset can be optained via hivelist or hivescan.

## printkey
`vol.py -f <image> --profile=<profile> printkey -K "<searchterm>"`

where `searchterm` should be something like `Microsoft\Windows NT\CurrentVersion` and should not include the hive name.

## dumpregistry
Dumps the registry from the memory image.