```
In the last challenge, you saw how XOR worked at the level of bits. In this one, we're going to cover the properties of the XOR operation and then use them to undo a chain of operations that have encrypted a flag. Gaining an intuition for how this works will help greatly when you come to attacking real cryptosystems later, especially in the block ciphers category.  
  
There are four main properties we should consider when we solve challenges using the XOR operator  
  
Commutative: A ⊕ B = B ⊕ A  
Associative: A ⊕ (B ⊕ C) = (A ⊕ B) ⊕ C  
Identity: A ⊕ 0 = A  
Self-Inverse: A ⊕ A = 0  
  
Let's break this down. Commutative means that the order of the XOR operations is not important. Associative means that a chain of operations can be carried out without order (we do not need to worry about brackets). The identity is 0, so XOR with 0 "does nothing", and lastly something XOR'd with itself returns zero.  
  
Let's put this into practice! Below is a series of outputs where three random keys have been XOR'd together and with the flag. Use the above properties to undo the encryption in the final line to obtain the flag.  
  
KEY1 = a6c8b6733c9b22de7bc0253266a3867df55acde8635e19c73313  
KEY2 ^ KEY1 = 37dcb292030faa90d07eec17e3b1c6d8daf94c35d4c9191a5e1e  
KEY2 ^ KEY3 = c1545756687e7573db23aa1c3452a098b71a7fbf0fddddde5fc1  
FLAG ^ KEY1 ^ KEY3 ^ KEY2 = 04ee9855208a2cd59091d04767ae47963170d1660df7f56f5faf
```

This challenge uses the fact that XOR is associative, i.e. (KEY1 ⊕ KEY2) ⊕ KEY3 is the same as KEY1 ⊕ (KEY2 ⊕ KEY3). We can use the following code to obtain the flag:

```python
#!/usr/bin/env python3

from Crypto.Util.number import *

KEY1 = 0xa6c8b6733c9b22de7bc0253266a3867df55acde8635e19c73313
KEY2_KEY1 = 0x37dcb292030faa90d07eec17e3b1c6d8daf94c35d4c9191a5e1e
KEY2_KEY3 = 0xc1545756687e7573db23aa1c3452a098b71a7fbf0fddddde5fc1
FLAG_KEY1_KEY3_KEY2 = 0x04ee9855208a2cd59091d04767ae47963170d1660df7f56f5faf

print(long_to_bytes(FLAG_KEY1_KEY3_KEY2 ^ KEY2_KEY3 ^ KEY1).decode())
```

**Note: This requires the installation of PyCryptodome. You can install it with the following command: `pip install pycryptodome` **

The code uses the variable `KEY2_KEY3` to XOR it with both the `KEY1`  and `FLAG_KEY1_KEY2_KEY3` variable. The output of that operation is the flag, but in long integer format. To turn it into readable text, we use `long_to_bytes()`.

We can think of this challenge as a simple equation:

`FLAG ⊕ KEY 1 ⊕ KEY2 ⊕ KEY3 = 0x04ee9855208a2cd59091d04767ae47963170d1660df7f56f5faf`

We are solving for the `FLAG` value so we simply move everything else to the other side:

`FLAG = 0x04ee9855208a2cd59091d04767ae47963170d1660df7f56f5faf ⊕ KEY1 ⊕ KEY2 ⊕ KEY3`

In normal equations the sign would change, but since XOR is self-inverse we can just apply the same operation again (i.e. XOR). Using the associative property of XOR we can write the equation as:

`FLAG = 0x04ee9855208a2cd59091d04767ae47963170d1660df7f56f5faf ⊕ KEY1 ⊕ (KEY2 ⊕ KEY3)`    **Note (KEY2 ⊕ KEY3) = KEY2_KEY3 = 0xc1545756687e7573db23aa1c3452a098b71a7fbf0fddddde5fc1**

Running the script (or calculating the equation) results in the flag: `crypto{x0r_i5_ass0c1at1v3}`