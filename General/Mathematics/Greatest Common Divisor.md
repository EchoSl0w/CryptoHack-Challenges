```
The Greatest Common Divisor (GCD), sometimes known as the highest common factor, is the largest number which divides two positive integers (a,b)(a,b).  
  
For a=12,b=8a=12,b=8 we can calculate the divisors of aa: {1,2,3,4,6,12}{1,2,3,4,6,12} and the divisors of bb: {1,2,4,8}{1,2,4,8}. Comparing these two, we see that gcd⁡(a,b)=4gcd(a,b)=4.  
  
Now imagine we take a=11,b=17a=11,b=17. Both aa and bb are prime numbers. As a prime number has only itself and 11 as divisors, gcd⁡(a,b)=1gcd(a,b)=1.  
  
We say that for any two integers a,ba,b, if gcd⁡(a,b)=1gcd(a,b)=1 then aa and bb are coprime integers.  
  
If aa and bb are prime, they are also coprime. If aa is prime and b<ab<a then aa and bb are coprime.  
  
Think about the case for aa prime and b>ab>a, why are these not necessarily coprime?  
  
There are many tools to calculate the GCD of two integers, but for this task we recommend looking up [Euclid's Algorithm](https://en.wikipedia.org/wiki/Euclidean_algorithm).  
  
Try coding it up; it's only a couple of lines. Use a=12,b=8a=12,b=8 to test it.  
  
Now calculate gcd⁡(a,b)gcd(a,b) for a=66528,b=52920a=66528,b=52920 and enter it below.
```

The challenge requires that we compute the Greatest Common Divisor. The following code does just that:

```python
#!/usr/bin/env python3

def custom_gcd(a, b):
    while b:
        a, b = b, a%b
    return a

print(custom_gcd(66528,52920))
```

For a more detailed proof of why this works, check out [this link](https://www.whitman.edu/mathematics/higher_math_online/section03.03.html) or [this link](https://proofwiki.org/wiki/Euclidean_Algorithm)

The flag is: `1512`