# Encryption - Symmetric

## Solution

Symmetric encryption (likely AES, DES, or simple cipher).

### Step 1: Identify Cipher Type
- Look for hints about algorithm
- Check ciphertext format
- Identify key/IV if provided

### Step 2: Common Symmetric Ciphers
- AES (Advanced Encryption Standard)
- DES (Data Encryption Standard)
- 3DES (Triple DES)
- RC4, Blowfish

### Step 3: Decrypt

```python
from Crypto.Cipher import AES
import base64

# Example AES decryption
key = b'sixteen byte key'
iv = b'initialization v'
ciphertext = base64.b64decode('encrypted_data')

cipher = AES.new(key, AES.MODE_CBC, iv)
plaintext = cipher.decrypt(ciphertext)
print(plaintext)
```

### Step 4: Try Online Tools
- CyberChef
- dcode.fr
- cryptii.com

### Flag

```
RM{decrypted_message}
```
