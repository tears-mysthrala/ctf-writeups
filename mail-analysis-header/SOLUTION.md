# Mail analysis - Header

## Solution

Email header analysis challenge.

### Step 1: View Email Headers
The challenge provides an email (.eml file or raw headers).

### Step 2: Analyze Headers

Key headers to check:
- `From:` - Sender address
- `To:` - Recipient
- `Subject:` - Subject line
- `Date:` - Send date/time  
- `Received:` - Mail server hops
- `X-Originating-IP:` - Sender IP
- `Message-ID:` - Unique ID
- `Return-Path:` - Reply address

```bash
# View headers
cat email.eml | grep -E "^(From|To|Subject|Received|X-)"
```

### Step 3: Find the Flag
Look for:
- Encoded strings in headers
- IP addresses
- Suspicious patterns
- Base64 encoded data

### Tools
- Text editor
- grep
- Email header analyzer tools

### Flag

```
RM{...}
```
