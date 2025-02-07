```
Modern cryptography involves code, and code involves coding. CryptoHack provides a good opportunity to sharpen your skills.  
  
Of all modern programming languages, Python 3 stands out as ideal for quickly writing cryptographic scripts and attacks. For more information about why we think Python is so great for this, please see the [FAQ](https://cryptohack.org/faq#python3).  
  
Run the attached Python script and it will output your flag.
```

Once again, there is no real "challenge" in this task. We are provided with a python script which when run outputs the flag.

Contents of the python script:
```python
#!/usr/bin/env python3

import sys
# import this

if sys.version_info.major == 2:
    print("You are running Python 2, which is no longer supported. Please update to Python 3.")

ords = [81, 64, 75, 66, 70, 93, 73, 72, 1, 92, 109, 2, 84, 109, 66, 75, 70, 90, 2, 92, 79]

print("Here is your flag:")
print("".join(chr(o ^ 0x32) for o in ords))
```

Since there is no challenge, I'll take the time to explain what the script does. The script first performs a check if we are using python2 or python3 with the `sys.version_info.major` (https://docs.python.org/3/library/sys.html#sys.version_info). The function returns a tuple who's first element is the version number, so both `sys_version_info[0]` and `sys.version_info.major` result in the same output.

After checking the version, the script creates an array containing numbers , which are used in the last line to perform a bitwise XOR (`^`) operation with the hexadecimal number `0x32` (`50` in decimal).

The script uses list comprehension to iterate over each element of the array and XOR it with `0x32`. The result of the operation is then transformed into a character via the `chr()` function (https://docs.python.org/3/library/functions.html#chr). Finally, the XOR'd value is joined to an empty string using the `"".join()` code.

The script, when ran, outputs the following flag: `crypto{z3n_0f_pyth0n}`