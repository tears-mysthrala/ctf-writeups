# AD Recon - Domain Controller

**Points**: 10 | **Difficulty**: Very easy

## Challenge Overview

Basic Active Directory reconnaissance to identify the Domain Controller.

## Tools

- `nslookup`
- `nmap`
- `ldapsearch`
- PowerShell

## Solution

### Method 1: DNS Lookup

```bash
# Query for DC
nslookup -type=srv _ldap._tcp.dc._msdcs.DOMAIN.COM

# Or
dig -t SRV _ldap._tcp.dc._msdcs.DOMAIN.COM
```

### Method 2: LDAP Query

```bash
ldapsearch -x -h <IP> -s base namingContexts
```

### Method 3: Nmap

```bash
nmap -p 389,636,88,3268 <subnet> --open
```

### Method 4: PowerShell (if internal)

```powershell
# Get DC
Get-ADDomainController

# Or using .NET
[System.DirectoryServices.ActiveDirectory.Domain]::GetCurrentDomain()
```

## What to Look For

- **DNS Records**: SRV records for _ldap._tcp
- **Ports**: 88 (Kerberos), 389 (LDAP), 636 (LDAPS)
- **Hostname**: Usually named DC01, DC1, etc.

## Flag

The flag is typically the DC hostname or FQDN.

```
RM{DC_NAME}
```
