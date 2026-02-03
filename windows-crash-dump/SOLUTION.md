# Windows - Crash Dump

**Points**: 45 | **Difficulty**: Medium

## Challenge Overview

Windows memory forensics challenge analyzing a crash dump file.

## Tools Required

- **Volatility** (volatility3)
- **WinDbg**
- **strings**

## Solution Steps

### 1. Identify OS Profile

```bash
vol.py -f MEMORY.DMP windows.info
```

### 2. List Processes

```bash
vol.py -f MEMORY.DMP windows.pslist
vol.py -f MEMORY.DMP windows.pstree
```

### 3. Scan for Suspicious Activity

```bash
# Network connections
vol.py -f MEMORY.DMP windows.netscan

# Command line arguments
vol.py -f MEMORY.DMP windows.cmdline

# DLL list
vol.py -f MEMORY.DMP windows.dlllist
```

### 4. Extract Artifacts

```bash
# Dump process memory
vol.py -f MEMORY.DMP windows.memmap --pid <PID> --dump

# Extract files
vol.py -f MEMORY.DMP windows.filescan
vol.py -f MEMORY.DMP windows.dumpfiles --pid <PID>

# Registry
vol.py -f MEMORY.DMP windows.registry.hivelist
```

### 5. Search for Flag

```bash
strings MEMORY.DMP | grep -i "RM{"
strings memory.dump | grep -i flag
```

## Common Volatility Plugins

- `windows.pslist` - Process list
- `windows.netscan` - Network connections
- `windows.filescan` - File objects
- `windows.registry.userassist` - User activity
- `windows.malfind` - Malware detection

## Flag

```
RM{memory_forensics_expert}
```
