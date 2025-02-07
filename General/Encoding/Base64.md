```
Another common encoding scheme is Base64, which allows us to represent binary data as an ASCII string using an alphabet of 64 characters. One character of a Base64 string encodes 6 binary digits (bits), and so 4 characters of Base64 encode three 8-bit bytes.  
  
Base64 is most commonly used online, so binary data such as images can be easily included into HTML or CSS files.  
  
Take the below hex string, _decode_ it into bytes and then _encode_ it into Base64.  
  
72bca9b68fc16ac7beeb8f849dca1d8a783e8acf9679bf9269f7bf  
  
In Python, after importing the base64 module with `import base64`, you can use the `base64.b64encode()` function. Remember to decode the hex first as the challenge description states.
```

This challenge requires that we take a hex string, convert it to bytes and then to base64. The following script does exactly that:

```python
#!/usr/bin/env python3

import base64

hex_string = '72bca9b68fc16ac7beeb8f849dca1d8a783e8acf9679bf9269f7bf'

byte_string = bytes.fromhex(hex_string)

print(base64.b64encode(byte_string).decode('utf-8'))
```

It takes the hex string and uses `bytes.fromhex()` to convert it to a byte string, the result of that is stored in a variable appropriately called `byte_string`. Finally, the string is converted to base64 using `base64.b64encode()`. 

The flag is: `crypto/Base+64+Encoding+is+Web+Safe/`