APL translation of [Ninety-Nine Prolog Problems](https://sites.google.com/site/prologsite/prolog-problems/1)

# Section 1: Prolog Lists

## Problem 1 (*)

*Find the last element of a vector*

```
      last 'abcde'
'd'
```

## Problem 2 (*)

*Find the last but one element of a vector*

```
      but_last 'abcde'
'c'
```

## Problem 3 (*)

*Find the K'th element of a vector*

```
      3 element_at 'abcde'
'c'
```

## Problem 4 (*)

*Find the number of elements of a vector*

```
      length 'abcde'
5
```

## Problem 5 (*)

*Reverse a vector*

```
      reverse 'abcde'
'edcba'
```

## Problem 6 (*)

*Find out whether a vector is palindrome* <br>
A vector is palindrome if it can be read forward or backward.

```
      is_palindrom 'radar'
1
      is_palindrom 3 1 4 1
0
```

## Problem 7 (**)

*Flatten a nested vector*

```
      flatten (3 (1 (4 1) 5) 9)
3 1 4 1 5 9
```

## Problem 8 (**)

*Eliminate consecutive duplicates in a vector* <br>
If a vector contains repeated elements they should be replaced with a single copy of the element. The order of the elements should not be changed.

```
      compress 'aaaabccaadeeee'
'abcade'
```

## Problem 9 (**)

*Pack consecutive duplicate elements of vector into sub-vectors* <br>
If a vector contains repeated elements they should be placed in separate sub-vectors.

```
      pack 'aaaabccaadeeee'
'aaaa' 'b' 'cc' 'aa' 'd' 'eeee'
```

## Problem 10 (*)

*Run-length encoding of a vector* <br>
Use the result of P9 to implement the so-called run-length encoding data compression method. <br>
Consecutive duplicates are encoded as (N E) where N is the number of duplicates of the element E.

```
      encode 'aaaabccaadeeee'
(4 'a') (1 'b') (2 'c') (2 'a') (1 'd') (4 'e')
```

## Problem 11 (*)

*Modified run-length encoding* <br>
Modify the result of P10 in such a way that if an element has no duplicates it is simply copied into the result vector. <br>
Only elements with duplicates are encoded as (N E).

```
      encode_mod 'aaaabccaadeeee'
(4 'a') 'b' (2 'c') (2 'a') 'd' (4 'e')
```

## Problem 12 (**)

Decode a run-length encoded vector. <br>
Given a run-length code vector generated as specified in P11, construct its uncompressed version.

```
      decode_mod (4 'a') 'b' (2 'c') (2 'a') 'd' (4 'e')
'aaaabccaadeeee'
```

## Problem 13 (**)

*Run-length encoding of a list (direct solution)* <br>
Implement the so-called run-length encoding data compression method directly. <br>
I.e. don't explicitly create the sub-vectors containing the duplicates, as in P9, but only count them. <br>
As in P11, simplify the result vector by replacing (1 E) by E.

```
      encode_dir 'aaaabccaadeeee'
(4 'a') 'b' (2 'c') (2 'a') 'd' (4 'e')
```

## Problem 14 (*)

*Duplicate the elements of a vector*

```
        duplicate 'abccd'
'aabbccccdd'
```

## Problem 15 (**)

*Duplicate the elements of a vector given number of times*

```
      3 replicate 'abc'
'aaabbbccc'
```

## Problem 16 (**)

*Drop every N'th element from a vector*

```
      3 drop_every 'abcdefghik'
'abdeghk'
```

## Problem 17 (*)

*Split a vector into two sub-vectors, given the length of the first sub-vector*

```
      3 split 'abcdefghik'
'abc' 'defghik'
```

## Problem 18 (**)

*Extract a slice from a vector* <br>
Given two indices, I and K, the slice is the vector containing the elements between the I'th and K'th element of the original vector (both limits included).

```
      3 7 slice 'abcdefghik'
'cdefg'
```

## Problem 19 (**)

*Rotate a vector N places to the left*

```
      3 rotate 'abcdefgh'
'defghabc'
      ¯2 rotate 1 2 3 4 5 6 7 8 9 10
9 10 1 2 3 4 5 6 7 8
```

## Problem 20 (*)

*Remove the K'th element from a vector*

```
      2 remove_at 'abcda'
'acd'
```

## Problem 21 (*)

*Insert an element at a given position into a vector*

```
      'alfa' insert_at 2 ⊢1⊂'abcd'
'a' 'alfa' 'b' 'c' 'd'
```
```
      ⍝ Operator syntax
      3 {⍺⍺ ⍵⍵ ⍵} 1 ⊢4
3 1 4
      3 (1 {⍺ ⍺⍺ ⍵⍵ ⍵} 4) 1
3 1 4 1      
```

## Problem 22 (*)

*Create a vector containing all integers within a given range*

```
      4 range 9
4 5 6 7 8 9
```

## Problem 23 (**)

*Extract a given number of randomly selected elements from a vector*

```
      3 rnd_select 'abcdefgh' ⍝ Result may be different
'eda'
```

### Problem 24 (*)

*Lotto: Draw N different random numbers from ⍳M*

```
      6 lotto 49 ⍝ Result may be different
23 1 17 33 21 37
```

## Problem 25 (*)

*Generate a random permutation of the elements of a vector*

```
      rnd_perm 'abcdef' ⍝ Result may be different
'badcef'
```

## Problem 26 (**)

*Generate the combinations of K distinct objects chosen from the N elements of a vector (via backtracking)*

```
      3 comb 'abcdef'
'abc'
'abd'
'abe'
...
'def'
```

## Problem 27.1 (**)

*Group the elements of a set into disjoint subsets. (via backtracking)* <br>
In how many ways can a group of 9 people work in 3 disjoint subgroups of 2, 3 and 4 persons?

```
      group 'aldo' 'beat' 'carla' 'david' 'evi' 'flip' 'gary' 'hugo' 'ida'
('aldo' 'beat') ('carla' 'david' 'evi') ('flip' 'gary' 'hugo' 'ida')
...
```

## Problem 27.2 (**)

*Generalize P27.1 in a way that we can specify a vector of group sizes*

```
      2 2 5 group 'aldo' 'beat' 'carla' 'david' 'evi' 'flip' 'gary' 'hugo' 'ida'
('aldo' 'beat') ('carla' 'david') ('evi' 'flip' 'gary' 'hugo' 'ida')
...
```

Note that we do not want permutations of the group members: (('aldo' 'beat') ...) is the same solution as (('beat' 'aldo') ...). <br>
However, we make a difference between (('aldo' 'beat') ('carla' 'david') ...) and (('carla' 'david') ('aldo' 'beat') ...). <br>
You may find more about this combinatorial problem searching ["Multinomial coefficients"](https://brilliant.org/wiki/multinomial-coefficients/).

## Problem 28.1 (**)

*Sort ascendingly a vector of vectors according their length*

```
      lsort 'abc' 'de' 'fgh' 'de' 'ijkl' 'mn' 'o'
'o' 'de' 'de' 'mn' 'abc' 'fgh' 'ijkl'
```

## Problem 28.2 (**)

*Sort ascendingly a vector of vectors according to their length frequency* <br>
Vectors with rare lengths are placed first, others with a more frequent length come later.

```
      lfsort 'abc' 'de' 'fgh' 'de' 'ijkl' 'mn' 'o'
'ijkl' 'o' 'abc' 'fgh' 'de' 'de' 'mn'
```
