# PadBuster.pl
#padding #oracle #crypto

Github: https://github.com/AonCyberLabs/PadBuster
Tutorial: https://medium.com/@mrkarthik07/i-know-mag1k-a-padding-oracle-attack-745d3b0bb2b1

## Basic Usage
`padbuster URL EncryptedSample BlockSize <options>`

## Decrypt cookie
`padBuster.pl <url> <cookie-val> <bitsize (8)> --cookies <auth>=<cookie-val>`

## Encrypt specific value as cookie
`padBuster.pl <url> <cookie-val> <bitsize (8)> --cookies <auth>=<cookie-val> -plaintext <desired-value>`
