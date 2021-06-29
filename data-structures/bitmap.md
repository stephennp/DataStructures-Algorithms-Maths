# Intro

- Working on bytes, or data types comprising of bytes like ints, floats, doubles or even data structures which stores large amount of bytes is normal for a programmer. In some cases, a programmer needs to go beyond this - that is to say that in a deeper level where the importance of `bits` is realized.

- `Operations` with bits are used in Data compression (data is compressed by converting it from one representation to another, to reduce the space) ,Exclusive-Or Encryption (an algorithm to encrypt the data for safety issues).
- In order to encode, decode or compress files we have to extract the data at `bit level`. Bitwise Operations are faster and closer to the system and sometimes optimize the program to a good level.

- We all know that `1 byte comprises of 8 bits (xxxx xxxx)` and any integer or character can be represented using bits in computers, which we call its binary form(contains only 1 or 0) or in its base 2 form.

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
# Binary or Bit
- In binary, each `binary digit` is called a `bit` and can only have one of two values: `one or zero (base 2)`

# Byte
- A byte is a group of `8` bits. A bit is the most basic unit and can be either 1 or 0. A byte is not just 8 values between 0 and 1, but `256` (28) different combinations (rather permutations) ranging from `00000000 via e.g. 01010101 to 11111111`. Thus, `one byte can represent a decimal number between 0(00) and 255`.

- `Puzzled`? Remember that 3 decimal numbers also don’t just stand for 3 values between 0 and 9, but `1000 (10^3) permutations from 0(00) to 999`.
## What is a buffer of bytes? 
- Think of buffer as just another word for an array, list, whatever resonates with your programming experience. Like a byte is a group of 8 bits, a buffer is a group of a pre-defined number of bytes. 
- If we have a group of 3 bytes, this could either represent 3 values between 0 and 255, but also one single value between `0 and 16777216 (256^3)`.


## How to send text? 
- The short answer is: `don’t`. 
- `Text uses a lot of bytes`. 
- Unicode defines more than 128000 characters, so that would take `3 bytes per character`! 
- There are rarely good reasons to use text instead of numbers, apart from maybe transmitting some user input.
-  Most of the time only the Alpha-numeric characters suffice, in that case you can get away by using ASCII characters that only use a single byte per character. Every string must be terminated with a NULL (0x00, ‘\0’) character to indicate the string has ended.
# Decimal
# Hexadecimal

- Often shortened to `hex`, is a numeral system made up of `16` symbols `(base 16)`. 
- 0,1,2,3,4,5,6,7,8,9,A, B, C, D, E and F
- Hexadecimal `A = decimal 10`, and hexadecimal `F = decimal 15`.
- For example, the three digit decimal value `219` requires eight bits to be represented in binary (11011011). Humans find reading, remembering, and typing long strings of bits inconvenient. Hexadecimal allows groups of four bits to be more conveniently represented by a single "hex" digit, so the eight bit binary value 11011011 only requires two hexadecimal digits `DB`
- To avoid confusion with decimal, octal or other numbering systems, hexadecimal numbers are sometimes written with a `h` after or `0x` before the number. For example, `63h` and `0x63` mean 63 hexadecimal.

|  Hex |        Binary       |  Octal | Decimal |
|:----:|:-------------------:|:------:|:-------:|
| 0    | 0                   | 0      | 0       |
| 1    | 1                   | 1      | 1       |
| 2    | 10                  | 2      | 2       |
| 3    | 11                  | 3      | 3       |
| 4    | 100                 | 4      | 4       |
| 5    | 101                 | 5      | 5       |
| 6    | 110                 | 6      | 6       |
| 7    | 111                 | 7      | 7       |
| 8    | 1000                | 10     | 8       |
| 9    | 1001                | 11     | 9       |
| A    | 1010                | 12     | 10      |
| B    | 1011                | 13     | 11      |
| C    | 1100                | 14     | 12      |
| D    | 1101                | 15     | 13      |
| E    | 1110                | 16     | 14      |
| F    | 1111                | 17     | 15      |
| 10   | 1 0000              | 20     | 16      |
| 11   | 1 0001              | 21     | 17      |
| 24   | 10 0100             | 44     | 36      |
| 5E   | 101 1110            | 136    | 94      |
| 100  | 1 0000 0000         | 400    | 256     |
| 3E8  | 11 1110 1000        | 1750   | 1000    |
| 1000 | 1 0000 0000 0000    | 10000  | 4096    |
| FACE | 1111 1010 1100 1110 | 175316 | 64206   |
|      |                     |        |         |

## Binary to hexadecimal
Changing a number from binary to hex uses a grouping method. The binary number is separated into groups of four digits starting from the right. These groups are then converted to hexadecimal digits as shown in the chart above for the hexadecimal numbers 0 through F. To change from hexadecimal, the reverse is done. The hex digits are each changed to binary and the grouping is usually removed.

|      Binary      | Groupings |      |      |      |  Hex |
|:----------------:|:---------:|:----:|:----:|:----:|:----:|
| 01100101         |           |      | 0110 | 0101 | 65   |
| 010010110110     |           | 0100 | 1011 | 0110 | 4B6  |
| 1101011101011010 | 1101      | 0111 | 0101 | 1010 | D75A |

- When the quantity of bits in a binary numbers is not a multiple of 4, it is padded with zeros to make it so. Examples:
  - binary 110 = 0110, which is 6 Hex.
  - binary 010010 = 00010010, which is 12 Hex.
## Hexadecimal to decimal

Example: 5Fh and 3425h to decimal, method 1

```
5Fh to decimal
Hex		Decimal
5Fh	=	( 5 x 16 )	+	( 15 x 1 )
    =	80	+	15
5Fh	=	95
 	
3425h to decimal
Hex		Decimal
3425h	=	( 3 x 4096 )	+	( 4 x 256 )	+	( 2 x 16)	+	( 5 x 1 )
=	12288	+	1024	+	32	+	5
3425h	=	13349

```


# Unsigned and Signed Binary Numbers

- Variables such as integers can be represent in two ways, i.e., signed and unsigned. 
  - `Signed` numbers use sign flag or can be distinguish between `negative values and positive values`.
  - Whereas `unsigned` numbers stored only positive numbers but `not negative numbers`.


## Unsigned numbers
- The range of unsigned binary number is from  `0 to (2^n-1)`.
- Range of unsigned binary number is from  0 to (2n-1). Therefore, range of 5 bit unsigned binary number is from  0 to (25-1) which is equal from minimum value 0 (i.e., 00000) to maximum value 31 (i.e., 11111).
## Signed Numbers
- Sign-Magnitude form : `(-)(2^(n-1)-1) to (+)(2^(n-1)-1).`
- For example, range of 6 bit Sign-Magnitude form binary number is from  `(2^5-1)  to (2^5-1)` which is equal from minimum value `-31 (i.e., 1 11111) to maximum value +31 (i.e., 0 11111)`. And zero (0) has two representation, -0 (i.e., 1 00000)  and +0 (i.e., 0 00000).
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

  | p   | q   | $p\wedge q$ |
  | --- | --- | ----------- |
  | T   | T   | T           |
  | T   | F   | F           |
  | F   | T   | F           |
  | F   | F   | F           |

```javascript
A = 5 = (101) 2 , B = 3 = (011) 2 A & B = (101) 2 & (011) 2= (001)  2 = 1
```

## OR ( | )

- Bitwise OR is also a binary operator that operates on two equal-length bit patterns, similar to bitwise AND. If both bits in the compared position of the bit patterns are 0, the bit in the resulting bit pattern is 0, otherwise 1.

  | p   | q   | $p\vee q$ |
  | --- | --- | --------- |
  | T   | T   | T         |
  | T   | F   | T         |
  | F   | T   | T         |
  | F   | F   | F         |

```javascript
A = 5 = (101)2 , B = 3 = (011)2
A | B = (101)2 | (011)2 = (111)2 = 7
```

## XOR ( ^ )

- Bitwise XOR also takes two equal-length bit patterns. If both bits in the compared position of the bit patterns are 0 or 1, the bit in the resulting bit pattern is 0, otherwise 1.

| p   | q   | $p\oplus q$ |
| --- | --- | ----------- |
| T   | T   | F           |
| T   | F   | T           |
| F   | T   | T           |
| F   | F   | F           |

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

# How to check if a given number is a power of 2 ?

- Consider a number N and you need to find if N is a power of 2. Simple solution to this problem is to repeated divide N by 2 if N is even. If we end up with a 1 then N is power of 2, otherwise not. There are a special case also. If N = 0 then it is not a power of 2

```csharp
// complexity : O(logn)
// return true if x is a power of 2, otherwise false.
 bool isPowerOfTwo(int x)
    {
        if(x == 0)
            return false;
        else
        {
            while(x % 2 == 0) x /= 2;
            return (x == 1);
            }
    }
```

- The same problem can be solved using bit manipulation. Consider a number x that we need to check for being a power for 2. Now think about the binary representation of `(x-1)`.
- `(x-1)` will have all the bits same as x, except for the rightmost 1 in x and all the bits to the right of the rightmost 1 (eg 000`1` & 100`1`)

```javascript
Let, x = 4 = (100)2
x - 1 = 3 = (011)2
Let, x = 6 = (110)2
x - 1 = 5 = (101)2
```

- Now think about x & (x-1). x & (x-1) will have all the bits equal to the x `except for the rightmost 1 in x`.

```javascript
Let, x = 4 = (100)2
x - 1 = 3 = (011)2
x & (x-1) = 4 & 3 = (100)2 & (011)2 = (000)2
Let, x = 6 = (110)2
x - 1 = 5 = (101)2
x & (x-1) = 6 & 5 = (110)2 & (101)2 = (100)2
```

- So if `x is a power of 2 then x & (x-1) will be 0`

```csharp
bool isPowerOfTwo(int x)
    {
        // x will check if x == 0 and !(x & (x - 1)) will check if x is a power of 2 or not
        return (x && !(x & (x - 1)));
    }
```

# Count the number of ones in the binary representation of the given number.
- The basic approach to evaluate the binary form of a number is to traverse on it and count the number of ones. But this approach takes log2N of time in every case.

- Why log2N ?
  - As to get a number in its binary form, we have to divide it by 2, until it gets 0, which will take log2N of time.

- With bitwise operations, we can use an algorithm whose running time depends on the number of ones present in the binary form of the given number. This algorithm is much better, as it will reach to logN, only in its worst case.
```csharp
    int count_one (int n)
        {
            while( n )
            {
            n = n&(n-1);
               count++;
            }
            return count;
    }
```
- Why this algorithm works ?
  - As explained in the previous algorithm, the relationship between the bits of `x and x-1`. So as in x-1, the rightmost 1 and bits right to it are flipped, then by performing x&(x-1), and storing it in x, will reduce x to a number containing number of ones(in its binary form) less than the previous state of x, thus increasing the value of count in each iteration.

- Example:
  ```
  n = 23 = {10111}2 .
  1. Initially, count = 0.
  2. Now, n will change to n&(n-1). As n-1 = 22 = {10110}2 , then n&(n-1) will be {101112 & {10110}2, which will be {10110}2 which is equal to 22. Therefore n will change to 22 and count to 1.
  3. As n-1 = 21 = {10101}2 , then n&(n-1) will be {10110}2 & {10101}2, which will be {10100}2 which is equal to 20. Therefore n will change to 20 and count to 2.
  4. As n-1 = 19 = {10011}2 , then n&(n-1) will be {10100}2 & {10011}2, which will be {10000}2 which is equal to 16. Therefore n will change to 16 and count to 3.
  5. As n-1 = 15 = {01111}2 , then n&(n-1) will be {10000}2 & {01111}2, which will be {00000}2 which is equal to 0. Therefore n will change to 0 and count to 4.
  6. As n = 0, the the loop will terminate and gives the result as 4.
  ```
- Complexity: `O(K)`, where K is the number of ones present in the binary form of the given number.

# Check if the ith bit is set in the binary form of the given number.
- To check if the ith bit is set or not (1 or not), we can use AND operator. How?

- Let’s say we have a number N, and to check whether it’s ith bit is set or not, we can AND it with the number `2^i` .
- The binary form of `2^i` contains only ith bit as set (or 1), else every bit is 0 there. When we will AND it with N, and if the ith bit of N is set, then it will return a non zero number (`2^i` to be specific), else 0 will be returned
- Using Left shift operator, we can write `2^i as 1 << i` . Therefore:
```csharp
bool check (int N)
    {
        if( N & (1 << i) )
            return true;
        else
            return false;
    }
```
- Example

- Let’s say N = 20 = {10100} (base) 2. Now let’s check if it’s 2nd bit is set or not(starting from 0). For that, we have to AND it with 2^2 = 1<<2 = {100}(base)2 .
- {10100} & {100} = {100} = 2^2 = 4(non-zero number), which means it’s `2nd bit is set`.

# How to generate all the possible subsets of a set ?
- A big advantage of bit manipulation is that it can help to iterate over all the subsets of an N-element set. As we all know there are 2^N possible subsets of any given set with N elements. What if we represent each element in a subset with a bit. A bit can be either 0 or 1, thus we can use this to denote whether the corresponding element belongs to this given subset or not. So each bit pattern will represent a subset.

- Consider a set A of 3 elements.
  ```A = {a, b, c}```

- Now, we need 3 bits, one bit for each element. 1 represent that the corresponding element is present in the subset, whereas 0 represent the corresponding element is not in the subset. Let’s write all the possible combination of these 3 bits.
```
0 = (000)2 = {}
1 = (001)2 = {c}
2 = (010)2 = {b}
3 = (011)2 = {b, c}
4 = (100)2 = {a}
5 = (101)2 = {a, c}
6 = (110)2 = {a, b}
7 = (111)2 = {a, b, c}
```
- Pseudo Code:
```csharp
possibleSubsets(A, N):
        for i = 0 to 2^N:
            for j = 0 to N:
                if jth bit is set in i:
                    print A[j]
            print ‘\n’
```            
- Implementation:
```csharp
  void possibleSubsets(char A[], int N)
    {
        for(int i = 0;i < (1 << N); ++i)
        {
            for(int j = 0;j < N;++j)
                if(i & (1 << j))
                    cout << A[j] << ‘ ‘;
            cout << endl;
        }
    }
```

# History of ASCII
- Both are stored in a byte (8 bits), but the original ASCII standard only defined the values 0–127 (ie, the lower 7 bits). The high bit, and thus the values 128–255, were left undefined.

- Why would anyone make a standard like that?

- In data transmission of the day, each bit took enough time to transmit that if you could only send 7 instead of 8, that was a 1/8th speed improvement.

- Since bytes with the high bit set were not valid ASCII data, some programs of the “8 bit era” used the high bit as a marker of some kind, so that a letter A with the high bit set might be considered a bolded A, or the first letter of a sentence, etc.

- But unfortunately, 7 bit ASCII didn’t contain characters useful for languages other than English, and by the 80’s, most computer manufacturers had added their own set of characters in the “high number” space - ATASCII for Atari, PETSCII for Commodore, etc. In many cases, these character sets included things like block graphics, playing card symbols (hearts, clubs, etc.), but there were no standards beyond 127.

- Eventually, the ISO group stepped in (see wikipedia’s Extended_ASCII article for a good discussion) and eventually we wound up with UTF-8 Unicode, which is a superset of ASCII-7, and a very popular encoding scheme (to say the least).

## ASCII Extended

Some clever people started using the 8th bit (the bit used for parity) to encode more characters to support their language (to support "é", in French, for example). Just using one extra bit doubled the size of the original ASCII table to map up to 256 characters (2^8 = 256 characters). And not 2^7 as before (128).
```
10000010 -> é (e with acute accent - 130)
10100000 -> á (a with acute accent - 160)
```
The name for this "ASCII extended to 8 bits and not 7 bits as before" could be just referred as "extended ASCII" or "8-bit ASCII".

## Unicode, The Rise

- ASCII Extended solves the problem for languages that are based on the Latin alphabet... what about the others needing a completely different alphabet? Greek? Russian? Chinese and the likes?

- We would have needed an entirely new character set... that's the rational behind Unicode. Unicode doesn't contain every character from every language, but it sure contains a gigantic amount of characters (see this table).

- You cannot save text to your hard drive as "Unicode". Unicode is an abstract representation of the text. You need to "encode" this abstract representation. That's where an encoding comes into play.

- Encodings: UTF-8 vs UTF-16 vs UTF-32

- This answer does a pretty good job at explaining the basics:

  - UTF-8 and UTF-16 are variable length encodings.
  - In UTF-8, a character may occupy a minimum of 8 bits.
  - In UTF-16, a character length starts with 16 bits.
  - UTF-32 is a fixed length encoding of 32 bits.
  - UTF-8 uses the ASCII set for the first 128 characters. That's handy because it means ASCII text is also valid in UTF-8.

- Mnemonics:

  - UTF-8: minimum 8 bits.
  - UTF-16: minimum 16 bits.
  - UTF-32: minimum and maximum 32 bits.