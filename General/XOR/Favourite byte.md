```
For the next few challenges, you'll use what you've just learned to solve some more XOR puzzles.  
  
I've hidden some data using XOR with a single byte, but that byte is a secret. Don't forget to decode from hex first.  
  
73626960647f6b206821204f21254f7d694f7624662065622127234f726927756d
```

This challenge is solved through brute forcing, as the possible key space is 2 to the power of 8 (i.e. 256). The script does the heavy work:

```python
#!/usr/bin/env python3

from Crypto.Util.number import *


def single_byte_xor(text: bytes, key: int) -> bytes:
    return bytes([b ^ key for b in text])


crypto_text = 0x73626960647f6b206821204f21254f7d694f7624662065622127234f726927756d

for i in range(256):
	output = (single_byte_xor(long_to_bytes(crypto_text), i))
	if b'crypto{' in output:
		print(output.decode())
```

I've ~~created~~ stolen the function `single_byte_xor` which takes a ciphertext and an integer and then perform XOR on all the bytes of the ciphertext with the integer key. The return value of the function is saved into the variable `output`, and the `if` statement compares if the byte string `crypto{` exists in the data, if so it's outputted to the screen. [Code stolen from this article](https://www.codementor.io/@arpitbhayani/deciphering-single-byte-xor-ciphertext-17mtwlzh30)

The flag is: `crypto{0x10_15_my_f4v0ur173_by7e}`