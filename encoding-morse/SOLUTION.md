# Encoding - Morse - Complete Solution

## Quick Summary

**Challenge**: Decode Morse code message
**Difficulty**: Very easy (5 points)
**Time**: ~10 minutes
**Skills**: Basic encoding, pattern recognition

## Challenge Text

The challenge presents a string of dots and dashes:

```
.__.
```

This is clearly Morse code encoding.

## Solution Steps

### Method 1: Online Decoder (Fastest)

1. Visit https://morsedecoder.com/
2. Paste the encoded string
3. Get instant decode

### Method 2: CyberChef

1. Go to https://gchq.github.io/CyberChef/
2. Drag "From Morse Code" operation
3. Paste input, get output

### Method 3: Python Script

```python
MORSE_CODE = {
    '.-': 'A', '-...': 'B', '-.-.': 'C', '-..': 'D',
    '.': 'E', '..-.': 'F', '--.': 'G', '....': 'H',
    '..': 'I', '.---': 'J', '-.-': 'K', '.-..': 'L',
    '--': 'M', '-.': 'N', '---': 'O', '.--.': 'P',
    '--.-': 'Q', '.-.': 'R', '...': 'S', '-': 'T',
    '..-': 'U', '...-': 'V', '.--': 'W', '-..-': 'X',
    '-.--': 'Y', '--..': 'Z',
    '-----': '0', '.----': '1', '..---': '2',
    '...--': '3', '....-': '4', '.....': '5',
    '-....': '6', '--...': '7', '---..': '8',
    '----.': '9'
}

def decode(morse):
    return ''.join(MORSE_CODE.get(c, '?') for c in morse.split())

# Use with challenge input
encoded = ".__."  # Example
decoded = decode(encoded)
print(f"RM{{{decoded}}}")
```

## Morse Code Basics

- **Dot (.)**: Short signal
- **Dash (-)**: Long signal (3x dot length)
- **Space**: Separates letters
- **/** or **|**: Separates words

Common letters:
- E = `.` (most common)
- T = `-`
- A = `.-`
- S = `...`
- O = `---`

## Flag Format

```
RM{DECODED_TEXT}
```

## References

- [Morse Code Chart](https://morsecode.world/international/morse.html)
- [CyberChef](https://gchq.github.io/CyberChef/)

