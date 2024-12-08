---
title: Home
layout: default
---

<script
  src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"
  type="text/javascript">
</script>

# Cryptography
## RSA 
### Background:
RSA(Rivest–Shamir–Adleman) is a asymmetric cryptosystem that uses prime numbers to ensure data communication. RSA hinges on the unique property of factoring such that it is very difficult to factor a large number when you don't know it's prime composition. In fact, it is proven that there does not exist an efficient non-quantum integer factorization algorithm.

#### Example 
Suppose we want to factor 2813, then you would check if 2813 is divisible by prime numbers until you find the first prime composition, 29 in this case. Now imagine if your first prime is large, then it would take a lot of computation time for a computer to find the first composition

### Operation:
RSA algorithm hinges around the following equation:
$$V_{sphere} = \frac{4}{3}\pi r^3$$