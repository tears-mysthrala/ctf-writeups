# SSRF - DNS Rebinding

**Platform**: [Root-me.pro](https://root-me.pro/)
**Category**: Web Security - Server Side Request Forgery
**Points**: 50
**Difficulty**: Medium
**Status**: ✅ Exploit Ready

## Challenge Description

For such a simplistic site, the protections in place seem rather robust. Demonstrate that they can still be bypassed by obtaining the flag on the site admin's profile page.

**Objective**: Access the `/admin` endpoint (localhost-only) via DNS rebinding attack to retrieve the flag.

**Flag Format**: `RM{...}`

## Quick Start

### Prerequisites
- Python 3.x
- `requests` library: `pip install requests`
- `dnspython` library: `pip install dnspython`
- Unrestricted network access (no DNS rebinding service blocking)

### Running the Exploit

```bash
# Main exploit (recommended)
python3 exploits/exploit_multi.py
```

Expected runtime: 5-20 minutes (50-200 attempts)

### If DNS Services Are Blocked

Try from:
1. **Mobile hotspot** (different ISP)
2. **Cloud VPS** (AWS/GCP/DigitalOcean)
3. **Different WiFi network**

Or use local DNS server (requires sudo):
```bash
sudo python3 exploits/dns_rebind_server.py
```

## Vulnerability

**Type**: TOCTOU (Time-of-Check-Time-of-Use) in DNS resolution

The application validates that a URL resolves to a public IP, then after a 0.5-second delay, makes the actual request. DNS rebinding exploits this timing window:

1. First DNS lookup → Returns public IP (8.8.8.8) → ✅ Passes validation
2. **0.5 second delay** → DNS TTL expires
3. Second DNS lookup → Returns localhost (127.0.0.1) → Accesses `/admin`

## File Structure

```
rootme-ssrf-dns-rebinding/
├── README.md              # This file
├── SOLUTION.md            # Complete technical write-up
├── FINAL_STATUS.md        # Implementation status & troubleshooting
└── exploits/
    ├── exploit_multi.py       # Main exploit (multiple DNS services)
    ├── exploit_final.py       # Parallel worker version
    ├── exploit_bypass.py      # SSRF bypass testing tool
    └── dns_rebind_server.py   # Local DNS rebinding server
```

## Documentation

- **[SOLUTION.md](./SOLUTION.md)** - Detailed vulnerability analysis and exploit development
- **[FINAL_STATUS.md](./FINAL_STATUS.md)** - Current status, blockers, and solutions

## Key Insights

### What Works ✅
- Exploit code is functional and tested
- Vulnerability confirmed via source code analysis
- All alternative SSRF bypasses correctly blocked

### Known Issues ⚠️
- Public DNS rebinding services (rbndr.us, rebind.network) may be blocked by some ISPs
- Requires network without DNS rebinding filtering
- VPN or sudo access helpful but not required

## Attack Flow

```
User Registration → Login → Profile Update with DNS Rebinding URL
                                        ↓
                            Server validates URL (public IP)
                                        ↓
                              [0.5 second delay]
                                        ↓
                          Server fetches URL (now localhost)
                                        ↓
                          /admin page → Profile picture
                                        ↓
                              Extract flag from base64
```

## Credits

- **Platform**: Root-me.pro
- **Analysis**: Claude Code
- **Exploit Development**: tears-mysthrala

## Disclaimer

This exploit is for authorized security testing and educational purposes only. Only use against systems you have explicit permission to test (such as CTF challenges).

---

**Last Updated**: 2026-02-02
