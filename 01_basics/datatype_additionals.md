# Integer(int)

- 0b111  : binary literal, equals 7 in decimal
- 0o17  : octal literal, equals 15 in decimal
- 0x1A  : hexadecimal literal, equals 25 in decimal
- 0b111  : binary literal, equals 7 in decimal

## Converting Between Bases
| Base        | Function | Example                |
| ----------- | -------- | ---------------------- |
| Binary      | `bin()`  | `bin(10)` → `'0b1010'` |
| Octal       | `oct()`  | `oct(10)` → `'0o12'`   |
| Hexadecimal | `hex()`  | `hex(255)` → `'0xff'`  |

```
from decimal import Decimal

# Example 1: More precise addition
a = Decimal('0.1')
b = Decimal('0.2')
c = a + b
print(c)   # Output: 0.3

# Example 2: Compare with float inaccuracy
print(0.1 + 0.2)               # Output: 0.30000000000000004
print(Decimal('0.1') + Decimal('0.2'))  # Output: 0.3

# Example 3: Decimal division
d = Decimal('1') / Decimal('3')
print(d)   # Output: 0.3333333333333333333333333333 (very precise)
```
```
from fractions import Fraction

# Example 1: Create fractions
f1 = Fraction(1, 3)
f2 = Fraction(2, 5)
print(f1)        # Output: 1/3
print(f2)        # Output: 2/5

# Example 2: Add fractions
result = f1 + f2
print(result)    # Output: 11/15

# Example 3: Convert float to fraction
f3 = Fraction(0.5)
print(f3)        # Output: 1/2

# Example 4: Automatically simplified
f4 = Fraction(8, 12)
print(f4)        # Output: 2/3
```

# String

## bytes: b'a\x01c' — Raw Bytes
- What it is:
  - A bytes object is a sequence of raw byte values (0–255), not characters.
  - Used for binary data like files, network packets, or low-level data manipulation.
  - Each byte is one unit of binary data, not necessarily readable text.

```
data = b'a\x01c'
print(list(data))  # Output: [97, 1, 99]

data = b'hello'
print(data.decode('utf-8'))  # Output: hello

data = b'\xff\xfe'
print(data.decode('utf-8'))  # Raises UnicodeDecodeError!

print(data.decode('utf-8', errors='replace'))  # Output: ��

b = b'ABC'
print(b.hex())  # Output: 414243

b = b'Name:\tAlice\nAge:\x1e'
print(b.decode('utf-8', errors='replace'))
# Output:
# Name:	Alice
# Age:�
```

## str (Unicode): u'sp\xc4m' — Text with Special Characters
- What it is:
  - A str object in Python 3 represents Unicode text.
  - Unicode supports international characters, like ä, ñ, Ω, etc.
  - The prefix u means Unicode string in Python 2.
  - In Python 3, all strings are Unicode by default, so the u prefix is optional and allowed but not necessary.

```
u'sp\xc4m' == 'spÄm'

print('\xc4')       # Output: Ä
print('\u00c4')     # Output: Ä
print(chr(196))     # Output: Ä

print(ord('Ä'))     # Output: 196
print(hex(ord('Ä')))  # Output: 0xc4
```

| Example      | Meaning | Explanation                           |
| ------------ | ------- | ------------------------------------- |
| `\x41`       | `'A'`   | 0x41 is 65 in decimal → `'A'`         |
| `\xc4`       | `'Ä'`   | 0xC4 is 196 in decimal → `'Ä'`        |
| `\u00c4`     | `'Ä'`   | Unicode escape for code point U+00C4  |
| `\u03A9`     | `'Ω'`   | Greek capital omega (U+03A9)          |
| `\U0001F600` | `'😀'`  | Full 8-digit Unicode escape for emoji |
