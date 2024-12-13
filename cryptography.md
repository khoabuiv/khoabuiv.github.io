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

### Operation:
RSA algorithm hinges around the following equation: <br>

$$(m^{e})^{d} \equiv m \mod n$$

<br>

Where: 
- $(n,e)$ is the public key pair
- $d$ is the private key. $d$ is a composite product of two prime numbers $p$ and $q$.
- $m$ is the plaintext message

Using this equations, we have the following operations:
