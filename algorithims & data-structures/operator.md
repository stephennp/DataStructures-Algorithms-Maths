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

Assume x=42, y=27


x&y = 0000 1010= 10 (in decimal)
 = 0011 1011= 59
 ^  = 0011 0001= 49
~ = 1101 0101
 = 1010 1000= 168. Notice, the bits are shifted 2 units to the left and the new bits are filled by 0s.
 = 0000 1010=10$$. Notice, the bits are shifted 2 units to the right and the new bits are filled by 0s.
For more information about how these operators work, see 