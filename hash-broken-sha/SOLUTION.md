# Hash - Broken SHA - Complete Solution

## Quick Summary

**Challenge**: Crack a SHA hash
**Difficulty**: Very easy (5 points)
**Time**: ~10 minutes
**Skills**: Hash cracking, rainbow tables

## Challenge Text

"Like a letter in the post office"

The challenge provides a hash to crack (likely MD5 or SHA-1).

## Solution Steps

### Step 1: Identify Hash Type

Check the hash length:
- 32 chars = MD5
- 40 chars = SHA-1
- 64 chars = SHA-256

```bash
echo -n "hash_here" | wc -c
```

### Step 2: Online Cracking (Recommended)

Use these free services:

1. **CrackStation**: https://crackstation.net/
   - Paste hash
   - Click "Crack Hashes"
   - Get result instantly

2. **Hashes.com**: https://hashes.com/en/decrypt/hash

3. **MD5Decrypt**: https://md5decrypt.net/

### Step 3: Offline Cracking

If online fails, use hashcat:

```bash
# For MD5
hashcat -m 0 -a 0 hash.txt /usr/share/wordlists/rockyou.txt

# For SHA-1  
hashcat -m 100 -a 0 hash.txt rockyou.txt

# For SHA-256
hashcat -m 1400 -a 0 hash.txt rockyou.txt
```

### Step 4: Verify and Submit

```python
import hashlib

# Verify the crack
plaintext = "found_password"
hash_check = hashlib.md5(plaintext.encode()).hexdigest()
print(f"Cracked: {plaintext}")
print(f"RM{{{plaintext}}}")
```

## Common Weak Hashes in CTFs

| Plaintext | MD5 Hash |
|-----------|----------|
| password | 5f4dcc3b5aa765d61d8327deb882cf99 |
| admin | 21232f297a57a5a743894a0e4a801fc3 |
| 123456 | e10adc3949ba59abbe56e057f20f883e |

## Hash Cracking Tools

- **Online**: CrackStation, Hashes.com
- **Offline**: hashcat, john
- **Rainbow Tables**: Pre-computed hash lookups

## Flag

```
RM{cracked_plaintext}
```

## Why "Broken"?

- MD5/SHA-1 are cryptographically broken
- Collision attacks possible
- Not recommended for security
- Perfect for CTF hash cracking!

