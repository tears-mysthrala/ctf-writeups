# CTF Write-ups & Exploits

Collection of CTF challenge solutions, write-ups, and exploit code.

## Repository Structure

```
ctf-writeups/
├── rootme-ssrf-dns-rebinding/    # Root-me.pro - SSRF DNS Rebinding (50pts)
│   ├── README.md                  # Challenge-specific documentation
│   ├── SOLUTION.md                # Technical solution write-up
│   ├── FINAL_STATUS.md            # Implementation status
│   └── exploits/                  # Exploit scripts
│       ├── exploit_multi.py       # Main exploit (recommended)
│       ├── exploit_final.py       # Parallel version
│       ├── exploit_bypass.py      # SSRF bypass testing
│       └── dns_rebind_server.py   # Local DNS rebinding server
└── ...                            # More challenges

```

## Challenges

### Root-me.pro

| Challenge | Category | Points | Status | Writeup |
|-----------|----------|--------|--------|---------|
| [SSRF - DNS Rebinding](./rootme-ssrf-dns-rebinding/) | Web Security | 50 | ✅ Solved | [Link](./rootme-ssrf-dns-rebinding/SOLUTION.md) |

## Usage

Each challenge directory contains:
- `README.md` - Challenge overview and quick start
- `SOLUTION.md` - Detailed technical write-up
- `exploits/` - Working exploit code
- Additional documentation as needed

## Contributing

This is a personal CTF repository. Feel free to fork and adapt for your own use.

## Disclaimer

All exploits and write-ups are for educational purposes only. Only use against systems you have explicit permission to test.

## Author

**tears-mysthrala** | 2026

---

*Write-ups generated with assistance from Claude Code*
