# Forensics Cheat-Sheet

## Registry
- [Registry](#registry)
  * [Registry Construct](#registry-construct)
  * [Hive-Overview](#hive-overview)
  
### Registry Construct
| | | | |
| --- | --- | --- | --- |
| HKCU\ | Software\ | Microsoft\Windws\CurrentVersion\ | Run |
| HIVE | Key | Subkeys | Key (with values) |

### Hive-Overview
| Location | Mountpoint |
| --- | --- | 
| %WinDir%\System32\Config\DEFAULT | HKEY_LOCAL_MASCHINE | 
| %WinDir%\System32\Config\SAM | HKEY_LOCAL_MASCHINE\SAM | 
| %WinDir%\System32\Config\SECURITY | HKEY_LOCAL_MASCHINE\SECURITY | 
| %WinDir%\System32\Config\SOFTWARE | HKEY_LOCAL_MASCHINE\SOFTWARE | 
| %WinDir%\System32\Config\SYSTEM | HKEY_LOCAL_MASCHINE\SYSTEM | 
| %UserProfile%\NTUSER.dat | HKEY_CURRENT_USER\ | 
| %UserProfile%\AppData\Local\Microsoft\Windows\UsrClass.dat | HKEY_CURRENT_USER\Software\Classes | 
