# FFUF
#FFUF

`/opt/ffuf/ffuf -w <wordlist> -u http://<domain>:<port>/FUZZ -e .php,.html,.js -c -r -ic >> <outfile>`

`ffuf -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-110000.txt -u http://trick.htb -H "Host: preprod-FUZZ.trick.htb" -fs 5480`

# gobuster
#gobuster
#wordlist

`gobuster dir -u http://blog-dev.travel.htb/ -w raft-large-words.txt -t 100`