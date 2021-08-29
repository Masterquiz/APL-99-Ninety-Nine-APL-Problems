APL translation of [Ninety-Nine Prolog Problems](https://sites.google.com/site/prologsite/prolog-problems/1)

# Section 1: Prolog Lists

## Problem 1 (*)

Find the last element of a vector.

#### Example
```
      last 'abcde'
'd'
      last 1 2 3 4 5
5
```

## Problem 2 (*)

Find the last but one element of a vector.

#### Example
```
      but_last 'abcde'
'c'
      but_last 1 2 3 4 5
4
```

## Problem 3 (*)

Find the K'th element of a vector.

#### Example
```
      3 element_at 'abcde'
'c'
      4 element_at 5 4 3 2 1
2
```

## Problem 4 (*)

Find the number of elements of a vector.

#### Example
```
      length 'abcde'
5
      length 1 2 3 4 5
5      
```

## Problem 5 (*)

Reverse a vector.

#### Example
```
      reverse 'abcde'
'edcba'
      reverse 1 2 3 4 5
5 4 3 2 1
```

## Problem 6 (*)

Find out whether a vector is palindrome. <br>
A vector is palindrome if it can be read forward or backward; e.g. 'radar'.

#### Example
```
      is_palindrom 'radar'
1
      is_palindrom 1 2 3 4
0
```

## Problem 7 (**)

Flatten a nested vector.

#### Example
```
      flatten (1 (2 (3 4) 5))
1 2 3 4 5 6 7 8 
      flatten ((⊂'a') ('b' (1⊂'c' 'd') 'e'))
'abcde'     
```

## Problem 8 (**)

Eliminate consecutive duplicates in a vector. <br>
If a vector contains repeated elements they should be replaced with a single copy of the element. The order of the elements should not be changed.

#### Example
```
      compress 'aaaabccaadeeee'
'abcade'
      compress 1 1 1 1 2 3 3 1 1 4 5 5 5 5
1 2 3 1 4 5
```

## Problem 9 (**)

Pack consecutive duplicate elements of vector into sub-vectors. <br>
If a vector contains repeated elements they should be placed in separate sub-vectors.

#### Example
```
      pack 'aaaabccaadeeee'
'aaaa' 'b' 'cc' 'aa' 'd' 'eeee'
      pack 1 1 1 1 2  3 3 1 1 4 5 5 5 5
(1 1 1 1) (2) (3 3) (1 1) (4) (5 5 5 5)
```

## Problem 10 (*)

Run-length encoding of a vector. <br>
Use the result of P9 to implement the so-called run-length encoding data compression method. <br>
Consecutive duplicates are encoded as (N E) where N is the number of duplicates of the element E.

#### Example
```
      encode 'aaaabccaadeeee'
(4 'a') (1 'b') (2 'c') (2 'a') (1 'd') (4 'e')
      encode 1 1 1 1 2 3 3 1 1 4 5 5 5 5
(4 1) (1 2) (2 3) (2 1) (1 4) (4 5)
```

## Problem 11 (*)

Modified run-length encoding. <br>
Modify the result of P10 in such a way that if an element has no duplicates it is simply copied into the result vector. <br>
Only elements with duplicates are encoded as (N E) .

#### Example
```
      encode_modified 'aaaabccaadeeee'
(4 'a') 'b' (2 'c') (2 'a') 'd' (4 'e')
      encode_modified 1 1 1 1 2 3 3 1 1 4 5 5 5 5
(4 1) 2 (2 3) (2 1) 4 (4 5)
```

## Problem 12 (**)

Decode a run-length encoded vector. <br>
Given a run-length code vector generated as specified in P11, construct its uncompressed version.

#### Example
```
      decode_modified (4 'a') 'b' (2 'c') (2 'a') 'd' (4 'e')
'aaaabccaadeeee'
      decode_modified (4 1) 2 (2 3) (2 1) 4 (4 5)
1 1 1 1 2 3 3 1 1 4 5 5 5 5
```

## Problem 13 (**)

Run-length encoding of a list (direct solution). <br>
Implement the so-called run-length encoding data compression method directly. <br>
I.e. don't explicitly create the sub-vectors containing the duplicates, as in P9, but only count them. <br>
As in P11, simplify the result vector by replacing (1 E) by E.

#### Example
```
      encode_direct 'aaaabccaadeeee'
(4 'a') 'b' (2 'c') (2 'a') 'd' (4 'e')
      encode_direct 1 1 1 1 2 3 3 1 1 4 5 5 5 5
(4 1) 2 (2 3) (2 1) 4 (4 5)
```

## Problem 14 (*)

Duplicate the elements of a vector.

#### Example
```
        duplicate 'abccd'
'aabbccccdd'   
        duplicate 1 2 3 3 4
1 1 2 2 3 3 3 3 4 4
```

## Problem 15 (**)

Duplicate the elements of a vector given number of times.

#### Example
```
      3 x_duplicate 'abc'
'aaabbbccc'
      3 x_duplicate 1 2 3
1 1 1 2 2 2 3 3 3
```

## Problem 16 (**)

Drop every N'th element from a vector.

#### Example
```
      3 drop_every 'abcdefghik'
'abdeghk'
      3 drop_every 10 9 8 7 6 5 4 3 2 1
10 9 7 6 5 4 3 2 1
```

## Problem 17 (*)

Split a vector into two sub-vectors, given the length of the first sub-vector.

#### Example
```
      3 split 'abcdefghik'
'abc' 'defghik'
      3 split 1 2 3 4 5 6 7 8 9 10
(1 2 3) (4 5 6 7 8 9 10)
```

## Problem 18 (**)

Extract a slice from a vector. <br>
Given two indices, I and K, the slice is the vector containing the elements between the I'th and K'th element of the original vector (both limits included).

#### Example
```
      3 7 slice 'abcdefghik'
'cdefg'
      3 7 slice 10 9 8 7 6 5 4 3 2 1
8 7 6 5 4
```

## Problem 19.1 (**)

Rotate a vector N places to the left.

#### Example
```
      3 rotate 'abcdefgh'
'defghikabc'
      ¯2 rotate 1 2 3 4 5 6 7 8 9 10
9 10 1 2 3 4 5 6 7 8
```
## Problem 19.2 (**)

Solve P19.1 using the result of P17.

## Problem 20 (*)

Remove the K'th element from a vector.

#### Example
```
      2 remove_at 'abcd'
'b' 'acd'
      2 remove_at 4 3 2 1
3 (4 2 1)
```

## Problem 21 (*)

Insert an element at a given position into a vector.

#### Example
```
      'alfa' insert_at 2 ⊢1⊂'a' 'b' 'c' 'd'
'a' 'alfa' 'b' 'c' 'd'
      (3 4) insert_at 3 ⊢(1 2) (5) (6 7 8)
(1 2) (5) (3 4) (6 7 8)
```

## Problem 22 (*)

Create a vector containing all integers within a given range.

#### Example
```
      range 4 9
4 5 6 7 8 9
```

## Problem 23 (**)

Extract a given number of randomly selected elements from a vector.

#### Example
```
      3 rnd_select 'abcdefgh' ⍝ Result may be different
'eda'
      3 rnd_select 1 2 3 4 5 6 ⍝ Result may be different
3 6 1
```

### Problem 24 (*)

Lotto: Draw N different random numbers from ⍳M.

#### Example
```
      6 lotto 49 ⍝ Result may be different
23 1 17 33 21 37
```

## Problem 25 (*)

Generate a random permutation of the elements of a vector.

#### Example
```
      rnd_permu 'abcdef' ⍝ Result may be different
'badcef'
      rnd_permu 1 2 3 4 5 6 ⍝ Result may be different
6 2 4 3 1 5
```

## Problem 26 (**)

Generate the combinations of K distinct objects chosen from the N elements of a vector (via backtracking).

#### Example
```
      3 combination 'abcdef'
'abc'
'abd'
'abe'
...
'def'
      4 combination 1 2 3 4 5
1 2 3 4
1 2 3 5
1 2 4 5
1 3 4 5
2 3 4 5
```

## Problem 27.1 (**)

Group the elements of a set into disjoint subsets. (via backtracking). <br>
In how many ways can a group of 9 people work in 3 disjoint subgroups of 2, 3 and 4 persons?

#### Example
```
      group 'aldo' 'beat' 'carla' 'david' 'evi' 'flip' 'gary' 'hugo' 'ida'
('aldo' 'beat') ('carla' 'david' 'evi') ('flip' 'gary' 'hugo' 'ida')
...
```

## Problem 27.2 (**)

Generalize P27.1 in a way that we can specify a vector of group sizes.

#### Example
```
      2 2 5 group 'aldo' 'beat' 'carla' 'david' 'evi' 'flip' 'gary' 'hugo' 'ida'
('aldo' 'beat') ('carla' 'david') ('evi' 'flip' 'gary' 'hugo' 'ida')
...
```

Note that we do not want permutations of the group members: (('aldo' 'beat') ...) is the same solution as (('beat' 'aldo') ...). <br>
However, we make a difference between (('aldo' 'beat') ('carla' 'david') ...) and (('carla' 'david') ('aldo' 'beat') ...). <br>
You may find more about this combinatorial problem searching ["Multinomial coefficients"](https://brilliant.org/wiki/multinomial-coefficients/).

## Problem 28.1 (**)

Sort ascendingly a vector of vectors according to length.

#### Example
```
      lsort 'abc' 'de' 'fgh' 'de' 'ijkl' 'mn' 'o'
'o' 'de' 'de' 'mn' 'abc' 'fgh' 'ijkl'
      lsort (1 2 3) (4 5) (6 7 8) (9 10) (11 12 13 14) (15 16)
(17) (4 5) (9 10) (15 16) (1 2 3) (6 7 8) (11 12 13 14)
```

## Problem 28.2 (**)

Sort ascendingly a vector of vectors according to their length frequency. Vectors with rare lengths are placed first, others with a more frequent length come later.

#### Example
```
      lsort 'abc' 'de' 'fgh' 'de' 'ijkl' 'mn' 'o'
'ijkl' 'o' 'abc' 'fgh' 'de' 'de' 'mn'
      lsort (1 2 3) (4 5) (6 7 8) (9 10) (11 12 13 14) (15 16)
(11 12 13 14) (17) (1 2 3) (6 7 8) (4 5) (9 10) (15 16) 
```
