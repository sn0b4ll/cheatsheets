# Registry Construct
| | | | |
| --- | --- | --- | --- |
| HKCU\ | Software\ | Microsoft\Windws\CurrentVersion\ | Run |
| HIVE | Key | Subkeys | Key (with values) |

# Hive-Overview
| Location | Mountpoint |
| --- | --- | 
| %WinDir%\System32\Config\DEFAULT | HKEY_LOCAL_MASCHINE | 
| %WinDir%\System32\Config\SAM | HKEY_LOCAL_MASCHINE\SAM | 
| %WinDir%\System32\Config\SECURITY | HKEY_LOCAL_MASCHINE\SECURITY | 
| %WinDir%\System32\Config\SOFTWARE | HKEY_LOCAL_MASCHINE\SOFTWARE | 
| %WinDir%\System32\Config\SYSTEM | HKEY_LOCAL_MASCHINE\SYSTEM | 
| %UserProfile%\NTUSER.dat | HKEY_CURRENT_USER\ | 
| %UserProfile%\AppData\Local\Microsoft\Windows\UsrClass.dat | HKEY_CURRENT_USER\Software\Classes | 

# Specific Artifacts
## MRU
| Name | Loction | Description |
| --- | --- | --- |
| OpenSaveMRU | HKCU/Software/Microsoft/Windows/CurrentVersion/Explorer/ComDIg32/OpenSaveMRU | Tracks files that have been opened or saved within a Windows shell dialog box. |
| LastVisitedMRU | HKCU/Software/Microsoft/Windows/CurrentVersion/Explorer&ComDIg32/LastVisitedMRU  | Tracks the specific executable used by an application to open the files documented in the OpenSaveMRU key and the directory location for the last file that was accessed by that application. |

Source: https://digital-forensics.sans.org/blog/2010/04/02/openrunsavemru-lastvisitedmru/
