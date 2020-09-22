# FFUF
#FFUF

`/opt/ffuf/ffuf -w <wordlist> -u http://<domain>:<port>/FUZZ -e .php,.html,.js -c -r -ic >> <outfile>`

# gobuster
#gobuster
#wordlist

`gobuster dir -u http://blog-dev.travel.htb/ -w raft-large-words.txt -t 100`