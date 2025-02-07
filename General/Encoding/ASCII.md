```
ASCII is a 7-bit encoding standard which allows the representation of text using the integers 0-127.  
  
Using the below integer array, convert the numbers to their corresponding ASCII characters to obtain a flag.  
  
[99, 114, 121, 112, 116, 111, 123, 65, 83, 67, 73, 73, 95, 112, 114, 49, 110, 116, 52, 98, 108, 51, 125]  
  
In Python, the `chr()` function can be used to convert an ASCII ordinal number to a character (the `ord()` function does the opposite).
```

This challenge requires that we convert the given numbers to their ASCII value. For that I created the following script:

```python
#!/usr/bin/env python3

ords = [99, 114, 121, 112, 116, 111, 123, 65, 83, 67, 73, 73, 95, 112, 114, 49, 110, 116, 52, 98, 108, 51, 125]

print("".join(chr(o) for o in ords))
```

Which uses list comprehension to join the ASCII letters that are produced by the `chr()` function.

The flag is: `crypto{ASCII_pr1nt4bl3}`