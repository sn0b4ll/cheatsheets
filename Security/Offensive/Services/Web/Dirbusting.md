#FFUF

`/opt/ffuf/ffuf -w <wordlist> -u http://<domain>:<port>/FUZZ -e .php,.html,.js -c -r -ic >> <outfile>`