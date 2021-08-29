APL translation of [Ninety-Nine Prolog Problems](https://sites.google.com/site/prologsite/prolog-problems/2)

# Section 2: Arithmetic

## Problem 1 (**)

*Determine whether a given integer number is prime*

```
      is_prime 27
1
      is_prime 1
0      
```

## Problem 2 (**)

*Determine the prime factors of a given positive integer* <br>
Construct a vector containing the prime factors in ascending order.

```
      prime_factors 315
3 3 5 7
```

## Problem 3 (**)

*Determine the prime factors of a given positive integer* <br>
Construct a vector of vectors containing the prime factors and their multiplicity.

```
      prime_factors_mult 315
(3 2) (5 1) (7 1)
```

## Problem 4 (*)

*Given a range of integers by its lower and upper limit, construct a vector of all prime numbers in that range*

```
      prime_list 3 11
3 5 7 11
```

## Problem 5 (**)

Goldbach's conjecture says that every positive even number greater than 2 is the sum of two prime numbers. E.g. 28 = 5 + 23. <br>
*Write a function to find the two prime numbers that sum up to a given even integer*

```
      goldbach 28
5 23
```

## Problem 6.1 (**)

*A list of Goldbach compositions*
Given a range of integers by its lower and upper limit, return a vector of all even numbers and their Goldbach composition.

```
      9 goldbach_list 18
(3 7) (5 7) (3 11) (3 13) (3 13) (5 13) ⍝ ←→ '10 = 3 + 7' '12 = 5 + 7' '14 = 3 + 11' '16 = 3 + 13' '18 = 5 + 13'
```

## Problem 6.2

In most cases, if an even number is written as the sum of two prime numbers, one of them is very small. <br>
Very rarely, the primes are both bigger than say 50. <br>
*Try to find out how many such cases there are in the range 2..3000*

## Problem 7 (**)

*Determine the greatest common divisor of two positive integer numbers (via Euclid's algorithm)*

```
      36 gcd 63
9
```

## Problem 8 (*)

*Determine whether two positive integer numbers are coprime* <br>
Two numbers are coprime if their greatest common divisor equals 1.

```
      35 are_coprime 64
1
      34 are_coprime 64
0      
```

## Problem 9 (**)

*Calculate Euler's totient function phi(m)* <br>
Euler's so-called totient function phi(m) is defined as the number of positive integers r (1 ≤ r < m) that are coprime to m. <br>
E.g. m = 10: r = 1 3 7 9; thus phi(m) = 4. Note the special case: phi(1) = 1. <br>
Find out what the value of phi(m) is if m is a prime number. (Use the most primitive method)

```
      phi_slow 10
4      
```

## Problem 10 (**)

*Calculate Euler's totient function phi(m)* <br>
If the list of the prime factors of a number m is known in the form of P3 then the function phi(m) can be efficiently calculated as follows: <br>
Let ((p1 m1) (p2 m2) (p3 m3) ...) be the vector of prime factors (and their multiplicities) of a given number m, then phi(m) can be calculated with the formula: <br>
```
      phi(m) = (p1 - 1) × (p1*m1 - 1) × (p2 - 1) × (p2*m2 - 1) × (p3 - 1) × (p3*m3 - 1) × ...
```

```
      phi_fast 10
4      
```

## Problem 11 (*)

*Compare the two methods of calculating Euler's totient function*

```
      ]runtime -c "phi_slow 10090" "phi_fast 10090"
```
