# HTML - Analyzer

## Solution

HTML source code analysis.

### Step 1: View Page Source

```
Right-click → View Page Source
Or press Ctrl+U
```

### Step 2: Search for Flag

```javascript
// Look for:
- HTML comments <!-- flag -->
- Hidden form fields
- JavaScript variables
- CSS with display:none
- Data attributes
```

### Step 3: Check All Resources

```bash
# Download and search
wget https://challenge-url
grep -r "RM{" .
grep -r "flag" .
```

### Tools
- Browser DevTools
- View Source
- grep
- curl

### Flag
Usually hidden in:
- HTML comments
- JavaScript code  
- Hidden divs
- Source code

```
RM{...}
```
