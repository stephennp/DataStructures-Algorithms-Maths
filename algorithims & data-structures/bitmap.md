# Intro
- Working on bytes, or data types comprising of bytes like ints, floats, doubles or even data structures which stores large amount of bytes is normal for a programmer. In some cases, a programmer needs to go beyond this - that is to say that in a deeper level where the importance of `bits` is realized.

- `Operations` with bits are used in Data compression (data is compressed by converting it from one representation to another, to reduce the space) ,Exclusive-Or Encryption (an algorithm to encrypt the data for safety issues).
- In order to encode, decode or compress files we have to extract the data at `bit level`. Bitwise Operations are faster and closer to the system and sometimes optimize the program to a good level.

- We all know that `1 byte comprises of 8 bits` and any integer or character can be represented using bits in computers, which we call its binary form(contains only 1 or 0) or in its base 2 form.

- Examples
```javascript
14 = {1110} base 2
= 1 * 2 ^3 + 1 * 2^2 + 1 * 2^1 + 0 * 2^0
= 14

20 = {10100 }base 2
= 1 * 2^4 + 0 * 2^3 + 1 * 2^2 + 0 * 2^1 + 0 * 2^0
= 20

// For characters, we use ASCII representation, which are in the form of integers which again can be represented using bits as explained above.
```
# Bitwise operators
- There are different bitwise operations used in the bit manipulation.
- These bit operations operate on the individual bits of the bit patterns. Bit operations are fast and can be used in optimizing time complexity. Some common bit operators are:

## NOT ( ~ )
- Bitwise NOT is an unary operator that flips the bits of the number i.e., if the ith bit is 0, it will change it to 1 and vice versa. Bitwise NOT is nothing but simply the one’s complement of a number. Lets take an example.

```javascript
N = 5 = (101) 2
~N = ~5 = ~(101) 2 = (010) 2 = 2
```

## AND ( & )
- Bitwise AND is a binary operator that operates on two equal-length bit patterns. If both bits in the compared position of the bit patterns are 1, the bit in the resulting bit pattern is 1, otherwise 0.

  | p | q | $p\wedge q$ |
  |---|---|-----|
  | T | T | T   |
  | T | F | F   |
  | F | T | F   |
  | F | F | F   |

```javascript
A = 5 = (101) 2 , B = 3 = (011) 2 A & B = (101) 2 & (011) 2= (001)  2 = 1
```
## OR ( | )
- Bitwise OR is also a binary operator that operates on two equal-length bit patterns, similar to bitwise AND. If both bits in the compared position of the bit patterns are 0, the bit in the resulting bit pattern is 0, otherwise 1.

  | p | q | $p\vee q$ |
  |---|---|-----|
  | T | T | T   |
  | T | F | T   |
  | F | T | T   |
  | F | F | F   |

```javascript
A = 5 = (101)2 , B = 3 = (011)2
A | B = (101)2 | (011)2 = (111)2 = 7
```
## XOR ( ^ )
- Bitwise XOR also takes two equal-length bit patterns. If both bits in the compared position of the bit patterns are 0 or 1, the bit in the resulting bit pattern is 0, otherwise 1.

 | p | q | $p\oplus q$ |
  |---|---|-----|
  | T | T | F   |
  | T | F | T   |
  | F | T | T   |
  | F | F | F   |
```javascript
A = 5 = (101)2 , B = 3 = (011)2
A ^ B = (101)2 ^ (011)2 = (110)2 = 6
```

## Left Shift ( << )
- Left shift operator is a binary operator which shift the some number of bits, in the given bit pattern, to the left and append 0 at the end.
- Left shift is equivalent to `multiplying` the bit pattern with `2^k` ( if we are shifting `k` bits ).
```javascript
1 << 1 = 2 => 2^1 * 1
1 << 2 = 4 => 2^2 * 1
1 << 3 = 8 => 2^3 * 1
1 << 4 = 16 => 2^4 * 1
2 << 4 => 2^4 *2 = 32
4 << 6 => 2^6 * 4 = 256
…
1 << n = 2^n * 1
```

## Right Shift ( >> )
- Right shift operator is a binary operator which shift the some number of bits, in the given bit pattern, to the right and append 1 at the end. 
- Right shift is equivalent to dividing the bit pattern with `2^k` ( if we are shifting `k` bits ).

```javascript
4 >> 1 = 2 => 4 / 2^1 = 2
6 >> 1 = 3 => 6/ 2^ 1 = 3
5 >> 1 = 2 => 5 / 2^1 = 2.5
16 >> 4 = 1 => 16 / 2 ^ 4 = 2
```
- Bitwise operators are good for saving space and sometimes to cleverly remove dependencies.
