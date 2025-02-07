```
XOR is a bitwise operator which returns 0 if the bits are the same, and 1 otherwise. In textbooks the XOR operator is denoted by ⊕, but in most challenges and programming languages you will see the caret `^` used instead.
```

| A   | B   | Output |
| --- | --- | ------ |
| 0   | 0   | 0      |
| 0   | 1   | 1      |
| 1   | 0   | 1      |
| 1   | 1   | 0      |
```
For longer binary numbers we XOR bit by bit: `0110 ^ 1010 = 1100`. We can XOR integers by first converting the integer from decimal to binary. We can XOR strings by first converting each character to the integer representing the Unicode character.  
  
Given the string `label`, XOR each character with the integer `13`. Convert these integers back to a string and submit the flag as `crypto{new_string}`.
```

To solve the challenge we only need to convert each letter in the string `label` to their decimal representation and XOR it with the number `13`. Python code for that:

```python
#!/usr/bin/env python3

cleartext = 'label'
xor_key = 13

xored_text = [chr(ord(letter) ^ xor_key) for letter in cleartext]

flag = "".join(xored_text)

print(flag)
```

I've used list comprehension to shorten the code. You can use `ord()` to convert each letter to their decimal representation, after performing XOR the code transforms the decimal value back to an ASCII letter and saves it into the variable `xored_text`. Finally, each letter is joined using `.join()` and saved to the variable `flag` which is outputted to the terminal

The flag is: `crypto{aloha}`