+++
author = "Moski Doski"
categories = ["weekly-challenge", "ruby", "python"]
date = 2018-12-30T19:42:37+04:00
description = "Week3"
draft = false
image = "images/2018/12/algorithm.png"
slug = "wc-week3"
tags = ["weekly-challenge", "ruby", "python"]
title = "Week3"

+++

This question is our first request question.

Given an even number (greater than 2), return two prime numbers whose sum will be equal to the given number.

Example:

```
Input: 4
Output: 2 + 2 = 4

```

If there are more than one solution possible, return the lexicographically smaller solution.

If `[a, b]` is one solution with `a <= b`, and `[c, d]` is another solution with `c <= d`, then

`[a, b] < [c, d]`

If `a < c` OR `a==c` AND `b < d`.

---

# Solution

Well, we know from mathmatics that a solution will always exists "[Goldbach’s conjecture"](https://en.wikipedia.org/wiki/Goldbach%27s_conjecture)

We can search for the smallest solution by iterating through possible values of the first potential prime. We check whether the first and second numbers are prime, and if so, return them.

```java
// java implementation
private static boolean isPrime(int n) {
    for (int i = 2; i < Math.sqrt(n); i++)
        if (n % i == 0)
            return false;
    return true;
}

public ArrayList<Integer> primesum(int a) {
    for (int i = 2; i <= a / 2; i++) {
        if (isPrime(i) && isPrime(a - i)) {
            ArrayList<Integer> output = new ArrayList<>();
            output.add(i);
            output.add(a - i);
            return output;
        }
    }

    return null;
}
```
``` python
# python implementation
def primesum(self, n):
    for i in xrange(2, n):
        if self.is_prime(i) and self.is_prime(n - i):
            return i, n - i

def is_prime(self, n):
    if n < 2:
        return False

    for i in xrange(2, int(n**0.5) + 1):
        if n % i == 0:
            return False

    return True
```