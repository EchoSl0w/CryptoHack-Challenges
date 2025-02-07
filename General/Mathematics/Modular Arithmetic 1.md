```
Imagine you lean over and look at a cryptographer's notebook. You see some notes in the margin:  
  
4 + 9 = 1  
5 - 7 = 10  
2 + 3 = 5  
  
At first you might think they've gone mad. Maybe this is why there are so many data leaks nowadays you'd think, but this is nothing more than modular arithmetic modulo 12 (albeit with some sloppy notation).  
  
You may not have been calling it modular arithmetic, but you've been doing these kinds of calculations since you learnt to tell the time (look again at those equations and think about adding hours).  
  
Formally, "calculating time" is described by the theory of congruences. We say that two integers are congruent modulo m if a ≡ b mod m.  
  
Another way of saying this, is that when we divide the integer aa by mm, the remainder is bb. This tells you that if mm divides aa (this can be written as m∣am∣a) then a≡0mod  ma≡0modm.  
  
Calculate the following integers:  
  
11 ≡ xmod  6  
8146798528947 ≡ y mod  17 
  
The solution is the smaller of the two integers, (x,y)(x,y), you obtained after reducing by the modulus.
```

The challenge requires that we perform modular arithmetic. The script as such is quite simple:

```python
#!/usr/bin/env python3

print(min(11%6, 8146798528947%17))
```

The solution is: `4`