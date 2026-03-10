# Introduction Challenges

This folder contains my solutions and notes for the "Introduction" section of CryptoHack.

The goal of these exercises is to understand the basics of Python and simple encoding techniques used in cryptography.

## Repository structure

Each challenge in this section has its own Python file.

These files contain only the code used to solve the challenge.

The README file documents the reasoning behind each solution:
- the goal of the challenge
- the method used to solve it
- the resulting flag.

This keeps the repository organized:
- `.py` files show the executable solution
- the README explains the reasoning.

---

## Great Snakes

**Goal:**  
Learn how to execute a Python script.

**Method:**  
The challenge provides a Python script (`great_snakes.py`).  
Executing the script with the Python interpreter prints the flag to the terminal.

The original file provided by CryptoHack was named
`great_snakes_35381fca29d68d8f3f25c9fa0a9026fb.py`.
It has been renamed here to `great_snakes.py` for clarity.

**Command used:**

```
python great_snakes.py
```

**Code:**

```python
print("crypto{z3n_0f_pyth0n}")
```

**Flag:**

```
crypto{z3n_0f_pyth0n}
```

---

## ASCII

**Goal:**  
Convert a list of integers into their corresponding ASCII characters.

**Method:**  
The challenge provides a list of integers.  
Each integer represents an ASCII character.

Using the Python function `chr()`, each number can be converted to the corresponding character.  
The characters are then concatenated to reconstruct the full string.

**Code:**

```python
a = ""

for x in [99, 114, 121, 112, 116, 111, 123, 65, 83, 67, 73, 73, 95, 112, 114, 49, 110, 116, 52, 98, 108, 51, 125]:
    a = a + chr(x)

print(a)

```
**Flag:**

```

crypto{ASCII_pr1nt4bl3}

```

---

## Hex

**Goal:**  
Decode a hexadecimal string into its original ASCII text.

**Method:**  
The challenge provides a string encoded in hexadecimal.  
Each pair of hexadecimal characters represents one byte.

Python provides the function `bytes.fromhex()` which converts a hexadecimal string into the corresponding bytes.

**Code:**

```python
print(bytes.fromhex("63727970746f7b596f755f77696c6c5f62655f776f726b696e675f776974685f6865785f737472696e67735f615f6c6f747d"))
```

**Flag:**

```
crypto{You_will_be_working_with_hex_strings_a_lot}
```
---

## Base64

**Goal:**  
Convert a hexadecimal string into Base64 encoding.

**Method:**  
The challenge provides a string encoded in hexadecimal.  
First, the hexadecimal string must be converted into bytes using Python's `bytes.fromhex()` function.  

Once the bytes are obtained, they can be encoded into Base64 using the `base64.b64encode()` function from the Python `base64` module.

**Code:**

```python
import base64

print(base64.b64encode(bytes.fromhex("72bca9b68fc16ac7beeb8f849dca1d8a783e8acf9679bf9269f7bf")))
```

**Flag:**

```
crypto/Base+64+Encoding+is+Web+Safe/
```
---

## Bytes and Big Integers

**Goal:**  
Convert a large integer back into the original message.

**Concept:**  
In cryptography, messages are often represented as integers.  
A sequence of ASCII bytes can be interpreted as a single large integer.

---

### Method 1 — Convert integer to hex

```python
hex(n)
```

Result:

```
0x63727970746f7b336e633064316e365f346c6c5f3768335f7734795f6430776e7d
```

Removing `0x` and decoding:

```python
bytes.fromhex("63727970746f7b336e633064316e365f346c6c5f3768335f7734795f6430776e7d")
```

---

### Method 2 — Using a cryptography library

Install dependency:

```
pip install pycryptodome
```

Solution:

```python
from Crypto.Util.number import long_to_bytes

n = 11515195063862318899931685488813747395775516287289682636499965282714637259206269

print(long_to_bytes(n))
```

---

**Flag**

```
crypto{3nc0d1n6_4ll_7h3_w4y_d0wn}
```
