# Local Priv Esc
https://gtfobins.github.io/
https://lolbas-project.github.io/#

1
# Sticky-Bit
2
```
3
find / -user root -perm -4000 -print 2>/dev/null
4
find / -perm -u=s -type f 2>/dev/null
5
find / -user root -perm -4000 -exec ls -ldb {} \;
6
```
7
​
8
# Exploit via Path if SUID-Binary does not use full path
9
https://www.hackingarticles.in/linux-privilege-escalation-using-path-variable/

# Exploit lxd group
https://www.hackingarticles.in/lxd-privilege-escalation/