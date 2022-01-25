# nmap
#recon #scanning #openports #ports #portscanning

Scan aggressively on all ports with OS detection, version detection, script scanning and traceroute and write to file
```
nmap -p- -T4 -oN <outfile> -A <IP> -v
nmap -p0-2000 -sU -T4 <IP> -v

```

## NSE-Scripts
Name | Link
--- | ---
Windows-RPC-Service | https://nmap.org/nsedoc/scripts/nfs-showmount.html