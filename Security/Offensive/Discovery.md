# Find Services
See [[nmap]].

# Find vHosts
#nmap
`nmap --script=http-vhosts --script-args=domain=<domain> -p80,443 -v <domain>`

  
#gobuster
`gobuster vhost --url http://horizontall.htb --wordlist subdomains-top1million-110000.txt`
Wordlist: https://github.com/danielmiessler/SecLists