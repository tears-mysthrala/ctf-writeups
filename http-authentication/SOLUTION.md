# HTTP - Authentication

## Solution

Basic HTTP authentication challenge.

### Step 1: Analyze the Challenge
The challenge presents a webpage protected by HTTP Basic Authentication.

### Step 2: Find Credentials
Check:
- Page source for hints
- Network tab for credentials
- Common defaults (admin:admin, admin:password)

### Step 3: Access Protected Page

```bash
# Using curl
curl -u username:password https://challenge-url

# Using browser
# Enter credentials when prompted
```

### Tools
- Browser DevTools
- Burp Suite
- curl

### Flag
Found in the protected page after authentication.

```
RM{...}
```
