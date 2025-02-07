```
When we encrypt something the resulting ciphertext commonly has bytes which are not printable ASCII characters. If we want to share our encrypted data, it's common to encode it into something more user-friendly and portable across different systems.  
  
Hexadecimal can be used in such a way to represent ASCII strings. First each letter is converted to an ordinal number according to the ASCII table (as in the previous challenge). Then the decimal numbers are converted to base-16 numbers, otherwise known as hexadecimal. The numbers can be combined together, into one long hex string.  
  
Included below is a flag encoded as a hex string. Decode this back into bytes to get the flag.  
  
63727970746f7b596f755f77696c6c5f62655f776f726b696e675f776974685f6865785f737472696e67735f615f6c6f747d  
  
In Python, the `bytes.fromhex()` function can be used to convert hex to bytes. The `.hex()` instance method can be called on byte strings to get the hex representation.
```

This challenge is similar to the previous one. In this case, the challenge requires that we convert a hex string to bytes (i.e. to a printable format). The following code does exactly that:

```python
#!/usr/bin/env python3

hex_string = "63727970746f7b596f755f77696c6c5f62655f776f726b696e675f776974685f6865785f737472696e67735f615f6c6f747d"

print(bytes.fromhex(hex_string).decode('utf-8'))
```

Here, I'm using the function `bytes.fromhex()` to transform the string to bytes which the `print()` function turns into readable text. I've added the `.decode('utf-8')` to make the text a bit prettier as that gets rid of the `b'random_text'` which indicates that it's a byte string.

The flag is: `crypto{You_will_be_working_with_hex_strings_a_lot}`