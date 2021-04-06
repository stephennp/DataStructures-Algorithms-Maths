# Intro

- Pre-requisite : Trie

- Suffix tree is a compressed trie of all the suffixes of a given string. Suffix trees help in solving a lot of string related problems like `pattern matching, finding distinct substrings` in a given string, finding longest palindrome etc. In this tutorial following points will be covered:

    - Compressed Trie
    - Suffix Tree Construction (Brute Force)
    - Brief description of Ukkonen's Algorithm

- Consider the following set of strings: { "banana", "nabd", "bcdef", "aaaaaa", "aaabaa"}
- A standard trie for the above set of strings will look like:

```					0
						a 	b n
				a			a 	c		a
			a			n	d		f		b
		a  b		a	e		e		 d
	a			a		n	f		g
a				 a	a
 ->

						0
	aaa				b			nabd
aaa baa	 anana	c
						def		feg
```	

# Explanation
```csharp
0 1 2 3 4
x y j x $

i=0, j=0   x--o
i=1, j=0   yx--o
i=1, j=1   yx--o--y
i=2, j=0  jyx--o
i=2, j=1  jyx--o--yj
i=2, j=2  jyx--o--yj
							|
							j
			   
i=3, j=0  xjyx--o--yj
								|
								j
			   
i=3, j=1  xjyx--o--yjx
								|
								j		
			   
i=3, j=2  xjyx--o--yjx
								|
							 jx		

// we do nothing , because x path already existed			   
i=3, j=3  xjyx--o--yjx
								| 
							 jx 

i=4, j=0  $xjyx--o--yjx
								| 
								jx 

i=4, j=1  $xjyx--o--yjx$
								| 
							 jx 
			   
i=4, j=2  $xjyx--o--yjx$
								| 
								jx$

i=4, j=3  $xjyx--o--yjx$
						 /  | 
						$   jx$ 				   
			   
									$
								 /
i=4, j=4  $xjyx--o--yjx$
						 /   | 
						$   jx$ 				   

=> convert to code like this
						 [4,4]
						    $ 
		     [1,4]		\ 			 [1,4]
i=4, j=4  $xjy <-[0,0]--o--yjx$ 
								/   | 
							[4,4]  [2,4]
								$     jx$ 			
			 
=> global end for leaves
									[4,end]
						  			$ 
		  	[1,end]		 / 			[1,end]
i=4, j=4  $xjy <-[0,0]--o--yjx$ 
								/   | 
						[4,end]  [2,end]
							$     jx$ 	

							
------------------------------------------------
			      			$a   a
										\ /
i=5, j=0->5  a$xjyx--o--yjx$a
								 /   | 
								$a   jx$a 			

										$ax ax
											\ /
i=6, j=0->6  xa$xjyx--o--yjx$ax
									/   | 
								$ax  jx$ax		
			
									y$ax  axy
											\ /
i=7, j=0->7  yxa$xjyx--o--yjx$axy
									 /   | 
								$axy  jx$axy	
							
										b y$axb axyb b
										\   \ /    /
i=8, j=0->8  byxa$xjyx---o-----yjx$axyb
										/    |      \ 
								$axyb jx$axyb    b  
			       
```
# Ref
- https://www.hackerearth.com/practice/data-structures/advanced-data-structures/suffix-trees/tutorial/