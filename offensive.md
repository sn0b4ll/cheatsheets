# Recon
Scan aggresivly on all ports with OS detection, version detection, script scanning and traceroute and write to file
```
nmap -p- -T4 -oN <outfile> -A <IP>
```

# Metasploit
local_exploit_suggester is really helpfull, but only on x86

## Correlation

Service | CVE | MSF-Module
--- | --- | ---
Samba 3.0.20 | [CVE-2007-2447](https://nvd.nist.gov/vuln/detail/CVE-2007-2447) | exploit/multi/samba/usermap_script
Windows <7| [CVE-2008-4250](https://nvd.nist.gov/vuln/detail/CVE-2008-4250) | exploit/windows/smb/ms08_067_netapi


# FTP
Try 
```
ftp <ip>
```
and use "anonymous" as name.

# Local Priv Esc
https://gtfobins.github.io/
