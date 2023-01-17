# Docker
#docker #lpe

## docker-escape
Dowload: https://github.com/PercussiveElbow/docker-escape-tool
`./docker-escape auto`

## by privs
Check privs inside container: `capsh --print`
Escape by privs https://blog.pentesteracademy.com/abusing-sys-module-capability-to-perform-docker-container-breakout-cf5c29956edd

## runc
https://github.com/Frichetten/CVE-2019-5736-PoC

## Root
If you are root, you can look at `fstab -l` and try to mount the host drive into the container.
