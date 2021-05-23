# Intro
- Operators are symbols that tell the compiler to perform specific mathematical or logical manipulations. In this tutorial , we will try to cover the most commonly used operators in programming.

- First, let's categorize them:
  1. Arithmetic
  2. Relational
  3. Bitwise
  4. Logical
  5. Assignment
  6. Increment
  7. Miscellaneous

# Arithmetic
| Symbol |	Operation |	Usage	Explanation |
| -- | -- | -- |
| +	 | addition	 | x+y | 	Adds values on either side of the operator | 
| -	 | subtraction | 	x-y | 	Subtracts the right hand operand from the left hand operand | 
| *	 | multiplication	 | x*y | 	Multiplies values on either side of the operator | 
| /	 | division | 	x/y | 	Divides the left hand operand by the right hand operand | 
| %	 | modulus	 | x%y	 | Divides the left hand operand by the right hand operand and returns remainder | 

# Relational Operators
- These operators are used for comparison. They return either true or false based on the comparison result. The operator '==' should not be confused with '='. The relational operators are as follows

| Symbol | 	Operation| 	Usage| 	Explanation | 
| -- | -- | -- | -- |
| ==| 	equal | 	x == y | 	Checks if the values of two operands are equal or not, if yes then condition becomes true. | 
| !=	| not equal | 	x != y | 	Checks if the values of two operands are equal or not, if values are not equal then condition becomes true. | 
| >	| greater than | 	x > y	 | Checks if the value of the left operand is greater than the value of the right operand, if yes then condition becomes true | 
| <	| less than	 | x < y | 	Checks if the value of the left operand is less than the value of the right operand, if yes then condition becomes true. | 
| >= | 	greater than or equal | 	x >= y | 	Checks if the value of the left operand is greater than or equal to the value of the right operand, if yes then condition becomes true. | 
| <= | 	less than or equal | 	x <= y | 	Checks if the value of the left operand is less than or equal to the value of the right operand, if yes then condition becomes true. | 

# Bitwise Operators
- These operators are very useful and we have some tricks based on these operators. These operators convert the given integers into binary and then perform the required operation, and give back the result in decimal representation.

| Symbol | 	Operation | 	Usage	Explanation | 
| -- | -- | -- |
| & | 	bitwise  AND  | 	x & y | 	Sets the bit to the result if it is set in both operands. | 
| or | 	bitwise  OR	 | x or y | 	Sets the bit to the result if it is set in either operand. | 
| ^ | 	bitwise  XOR | 	x ^ y	 | Sets the bit if it is set in one operand but not both | 
| ~ | 	bitwise  NOT | 	~x	 | Unary operator and has the effect of 'flipping' bits,i.e, flips 1 to 0 and 0 to 1. | 
| << | 	left shift | 	x << y	 | The left operand's value is moved left by the number of bits specified by the right operand. It is equivalent to multiplying x by 2^Y  | 
| >> | 	right shift	x >> y	 | The left operand's value is moved right by the number of bits specified by the right operand.It is equivalent to dividing x by 2^Y  | 

- Examples
```csharp
Assume x=42, y=27
x = 00101010
y = 00011011

x&y = 0000 1010= 10 (in decimal)
x|y = 0011 1011= 59
x^y  = 0011 0001= 49
~x = 1101 0101
x <<2 = 1010 1000= 168. //Notice, the bits are shifted 2 units to the left and the new bits are filled by 0s.
x >>2= 0000 1010=10$$. //Notice, the bits are shifted 2 units to the right and the new bits are filled by 0s.

```
#  Assignment Operators
| Symbol | 	Operation | 	Usage	 | Equivalence | 	Explanation | 
| -- | -- | -- | -- | -- |
| =	| assignment	| x = y	 | 	Assigns value from the right side operand(s) to the left side operand. | 
| += | add and assignment | 	x += y | 	x = x+y | 	Adds the right side operand to the left side operand and assigns the result to the left side operand. | 
| -= | 	subtract and assignment | 	x -= y | 	x= x-y | 	Subtracts the right side operand from the left side operand and assigns the result to the left side operand. | 
| `*=` | multiply and assignment |	x `*=` y | 	x= x*y | 	Multiplies the right side operand with the left side operand and assigns the result to the left side operand. | 
| /= | 	divide and assignment	 | x /= y | 	x= x/y	Divides the left side operand with the right side operand and assigns the result to the left side operand. | 
| %= | 	modulus and assignment | 	x%=y | 	x= x%y | 	Takes modulus using the two operands and assigns the result to the left side operand. | 
| <<=	 | left shift and assignment | 	x<<=y	 | x= x<< y | 	Shifts the value of x by y bits towards the left and stores the result back in x. | 
| >>= | 	right shift and assignment	 | x>>=y | 	x= x>>y | 	Shifts the value of x by y bits towards the right and stores the result back in x. | 
| &= | 	bitwise AND and assignment | 	x&=y | 	x= x&y | 	Does x&y and stores result back in x. | 
| or= | 	bitwise OR and assignment	 | xor=y	 | x= xory	 | Does xory and stores result back in x | 
| ^= | 	bitwise XOR and assignment	 | x^=y	 | x= x^y | 	Does x^y and stores result back in x. | 

# Increment/Decrement Operators
| Symbol |	Operation |		Usage	 |	Explanation |	
| -- | -- | -- | -- |
| ++ |		Postincrement |		x++	 |	Increment x by 1 after using its value |	
| -- |		Postdecrement |		x-- |		Decrement x by 1 after using its value |	
| ++ |		Preincrement |		++x |		Increment x by 1 before using its value |	
| -- |		Predecrement |		--x	 |	Decrement x by 1 before using its value |	

```
Examples:
Let x=10
then, after y=x++; y=10 and x=11, this is because x is assigned to y before its increment.
but if we had written y=++x; y=11 and x=11, because x is assigned to y after its increment.
Same holds for decrement operators.
```
# Operator Precedence
-  The following table describes the precedence order of the operators mentioned above. Here, the operators with the highest precedence appear at the top and those with the lowest at the bottom. In any given expression, the operators with higher precedence will be evaluated first.
  - LR= Left to Right
  - RL=Right to Left

| Category	| Associativity |	Operator |
| -- | -- | -- |
 | Postfix | 	LR | 	++  | -- | 
 | Unary | 	RL | 	+ - ! ~ ++ -- | 
 | Multiplicative | 	LR | 	* / % | 
 | Additive	 | LR	 | + - | 
 | Shift | 	LR | 	<< >> | 
 | Relational	 | LR | 	< <= > >= | 
 | Equality | 	LR | 	== != | 
 | Bitwise AND	 | LR	 | & | 
 | Bitwise XOR	 | LR	 | ^ | 
 | Bitwise OR	 | LR	 | `or` | 
 | Logical AND | 	LR | 	&& | 
 | Logical OR | 	LR | 	`or or` | 
 | Conditional | 	RL | 	?: | 
 | Assignment | 	RL | 	= += -= *= /= %= >>= <<= &= ^= `or=` | 