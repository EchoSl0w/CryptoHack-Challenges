```
Cryptosystems like RSA works on numbers, but messages are made up of characters. How should we convert our messages into numbers so that mathematical operations can be applied?  
  
The most common way is to take the ordinal bytes of the message, convert them into hexadecimal, and concatenate. This can be interpreted as a base-16/hexadecimal number, and also represented in base-10/decimal.  
  
To illustrate:  
  
message: HELLO  
ascii bytes: [72, 69, 76, 76, 79]  
hex bytes: [0x48, 0x45, 0x4c, 0x4c, 0x4f]  
base-16: 0x48454c4c4f  
base-10: 310400273487  
  
Python's PyCryptodome library implements this with the methods `bytes_to_long()` and `long_to_bytes()`. You will first have to install PyCryptodome and import it with `from Crypto.Util.number import *`. For more details check the [FAQ](https://cryptohack.org/faq/#install).  
  
Convert the following integer back into a message:  
  
11515195063862318899931685488813747395775516287289682636499965282714637259206269
```

This challenge requires that we convert an integer back into a string. You can use the following code to achieve that:

```python
#!/usr/bin/env python3

from Crypto.Util.number import *

very_long_int = 11515195063862318899931685488813747395775516287289682636499965282714637259206269

print(long_to_bytes(very_long_int).decode('utf-8'))
```

**Note: This requires the installation of PyCryptodome. You can install it with the following command: `pip install pycryptodome` **

The code uses the function `long_to_bytes()` which converts an integer to a byte string using big endian encoding. As you can see, the result of these operations is a byte string, to get rid of the `b'some_string'` I've used `.decode('utf-8')`

The flag is: `crypto{3nc0d1n6_4ll_7h3_w4y_d0wn}`