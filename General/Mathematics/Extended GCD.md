```
Let a and b be positive integers.  
  
The extended Euclidean algorithm is an efficient way to find integers u,v such that  
  
a⋅u+b⋅v=gcd⁡(a,b)a⋅u+b⋅v=gcd(a,b)  
  
Later, when we learn to decrypt RSA ciphertexts, we will need this algorithm to calculate the modular inverse of the public exponent.  
  
Using the two primes p=26513,q=32321p=26513,q=32321, find the integers u,v such that  
  
p⋅u+q⋅v=gcd⁡(p,q)p⋅u+q⋅v=gcd(p,q)  
  
Enter whichever of u and v is the lower number as the flag.  
  
Knowing that p,q are prime, what would you expect gcd⁡(p,q)gcd(p,q) to be? For more details on the extended Euclidean algorithm, check out [this page](https://web.archive.org/web/20230511143526/http://www-math.ucdenver.edu/~wcherowi/courses/m5410/exeucalg.html).
```

Code shamelessly stolen from https://github.com/ImperialCollegeLondon/Mathematical-Computing-Demo/blob/master/M1C%20(Python)/M1C-Number-Theory/.ipynb_checkpoints/Python%20Number%20Theory%2003%20-%20Extended%20Euclidean%20Algorithm-checkpoint.ipynb

```python
#!/usr/bin/env python3

def ehcf(a,b):
    # Initialization
    p1 = 1
    q1 = 0
    h1 = a
    p2 = 0
    q2 = 1
    h2 = b
    
    # Loop
    while h2 != 0:
        r = h1//h2
        p3 = p1 - r*p2
        q3 = q1 - r*q2
        h3 = h1 - r*h2
        p1 = p2
        q1 = q2
        h1 = h2
        p2 = p3
        q2 = q3
        h2 = h3

    # Output
    return [p1, q1, h1]

print(ehcf(26513, 32321))
```

Honestly, this went over my head

The flag is: `-8404`