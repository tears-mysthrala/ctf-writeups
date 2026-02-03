# API - Information Disclosure

**Points**: 10 | **Difficulty**: Very easy

## Challenge Overview

REST API exposing sensitive information through improper access controls.

## Vulnerability

Information disclosure via:
- Verbose error messages
- Debug endpoints
- Unrestricted API endpoints
- Excessive data in responses

## Solution Steps

### 1. Enumerate Endpoints

```bash
# Common API paths
curl https://api.example.com/api/v1/users
curl https://api.example.com/api/debug
curl https://api.example.com/api/config
curl https://api.example.com/swagger.json
curl https://api.example.com/.well-known/
```

### 2. Analyze Responses

```bash
# Pretty print JSON
curl https://api.example.com/api/users | jq .

# Look for sensitive data
curl https://api.example.com/api/users/me | jq .
```

### 3. Test Different Methods

```bash
# GET
curl -X GET https://api.example.com/api/admin

# OPTIONS (shows allowed methods)
curl -X OPTIONS https://api.example.com/api/users -i

# Check headers
curl -I https://api.example.com/api/
```

### 4. Common Information Leaks

- User enumeration
- Email addresses
- Internal IPs
- Version information
- Stack traces
- Database schema

## Tools

- `curl`
- `Postman`
- `Burp Suite`
- `ffuf` (API fuzzing)

## Example Finding

```json
{
  "user": {
    "id": 1,
    "username": "admin",
    "email": "admin@example.com",
    "role": "administrator",
    "flag": "RM{api_disclosure_found}",
    "internal_ip": "192.168.1.100"
  }
}
```

## Flag

```
RM{...}
```
