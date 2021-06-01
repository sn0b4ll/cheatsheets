# SNMP

## snmpcheck
#snmpbrute
Check for possible community-strings if permissions are very loose:
`snmp-check <ip>`

## snmpbrute
https://github.com/SECFORCE/SNMP-Brute/blob/master/snmpbrute.py
`python2 snmpbrute.py -t <target> -b`

## snmpwalk
#snmpwalk
Get version via snmpbrute
`snmpwalk -v 2c -c public pit.htb`

## snmpbw.pl
https://github.com/dheiland-r7/snmp
Faster alternative to snmpwalk.
`perl snmpbw.pl pit.htb public 2 1`

If `NetAddr:IP` is not installed, run
`cpan -i NetAddr::IP`