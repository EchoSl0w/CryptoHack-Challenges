```
As we've seen in the encoding section, cryptography involves dealing with data in a wide variety of formats: big integers, raw bytes, hex strings and more. A few structured formats have been standardised to help send and receive cryptographic data. It helps to be able to recognise and manipulate these common data formats.  
  
PEM is a popular format for sending keys, certificates, and other cryptographic material. It looks like:  
  
-----BEGIN RSA PUBLIC KEY-----  
MIIBCgKC... _(a whole bunch of base64)_  
-----END RSA PUBLIC KEY-----  
  
It wraps base64-encoded data by a one-line header and footer to indicate how to parse the data within. Perhaps unexpectedly, it's important for there to be the correct number of hyphens in the header and footer, otherwise cryptographic tools won't be able to recognise the file.  
  
The data that gets base64-encoded is DER-encoded ASN.1 values. Confused? The resources linked below have more information about what these acronyms mean but the complexity is there for historical reasons and going too deep into the details may drive you insane.  
  
Extract the private key d as a decimal integer from this PEM-formatted RSA key.
```

The challenge requires that we extract the private key `d`. To do that we can use `pyCryptodome`:

```python
from Crypto.PublicKey import RSA

with open("key.pem", "rb") as f:
    data = f.read()

mykey = RSA.import_key(data)
print(mykey.d)
```

The solution is: `15682700288056331364787171045819973654991149949197959929860861228180021707316851924456205543665565810892674190059831330231436970914474774562714945620519144389785158908994181951348846017432506464163564960993784254153395406799101314760033445065193429592512349952020982932218524462341002102063435489318813316464511621736943938440710470694912336237680219746204595128959161800595216366237538296447335375818871952520026993102148328897083547184286493241191505953601668858941129790966909236941127851370202421135897091086763569884760099112291072056970636380417349019579768748054760104838790424708988260443926906673795975104689`