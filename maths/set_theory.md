# Intro of Set theory
- A Set is an unordered collection of objects, known as elements or members of the set.
An element ‘a’ belong to a set A can be written as `a ∈ A`,  `a ∉ A` denotes that a is not an element of the set A.
- Representation of a Set
A set can be represented by various methods. 3 common methods used for representing set:
1. Statement form.
2. Roaster form or tabular form method.
3. Set Builder method.

## Statement form
In this representation, the well-defined description of the elements of the set is given. Below are some examples of the same.
1. The set of all even number less than 10.
2. The set of the number less than 10 and more than 1.

## Roster form
In this representation, elements are listed within the pair of brackets {} and are separated by commas. Below are two examples.
1. Let N is the set of natural numbers less than 5.
N = { 1 , 2 , 3, 4 }.

2. The set of all vowels in the English alphabet.
V = { a , e , i , o , u }.

## Set builder form
In Set-builder set is described by a property that its member must satisfy.
1. {x : x is even number divisible by 6 and less than 100}.
2. {x : x is natural number less than 10}.

 
## Equal sets
Two sets are said to be equal if both have same elements. For example A = {1, 3, 9, 7} and B = {3, 1, 7, 9} are equal sets.
 
## Subset

A set A is said to be subset of another set B if and only if every element of set A is also a part of other set B.
Denoted by ‘⊆‘.
‘A ⊆ B ‘ denotes A is a subset of B.

To prove A is the subset of B, we need to simply show that if x belongs to A then x also belongs to B.
To prove A is not a subset of B, we need to find out one element which is part of set A but not belong to set B.

## Power Sets
The power set is the set all possible subset of the set S. Denoted by P(S).
Example: What is the power set of {0,1,2}?
Solution: All possible subsets
{∅}, {0}, {1}, {2}, {0,1}, {0,2}, {1,2}, {0,1,2}.
Note: Empty set and set itself is also the member of this set of subsets.

Cardinality of power set is

$2^n$

, where n is the number of elements in a set.

## Cartesian Products
Let A and B be two sets. Cartesian product of A and B is denoted by A × B, is the set of all ordered pairs (a,b), where a belong to A and b belong to B.

$A × B = {(a, b) | a ∈ A ∧ b ∈ B}$.

Example 1. What is Cartesian product of A = {1,2} and B = {p, q, r}.
Solution : A × B ={(1, p), (1, q), (1, r), (2, p), (2, q), (2, r) };


The cardinality of A × B  is N*M, where N is the Cardinality of A and M is the cardinality of B.

Note: A × B is not the same as B × A.

## Union
Union of the sets A and B, denoted by A ∪ B, is the set of distinct element belongs to set A or set B, or both.

Example : Find the union of A = {2, 3, 4} and B = {3, 4, 5};
Solution : A ∪ B = {2, 3, 4, 5}.

## Intersection
The intersection of the sets A and B, denoted by `A ∩ B`, is the set of elements belongs to both A and B i.e. set of the common element in A and B.
Example: Consider the previous sets A and B. Find out A ∩ B.
Solution : A ∩ B = {3, 4}.

## Disjoint
Two sets are said to be disjoint if their intersection is the empty set .i.e sets have no common elements.
For Example
Let A = {1, 3, 5, 7, 9} and B = { 2, 4 ,6 , 8} .
A and B are disjoint set both of them have no common elements.

## Set Difference
Difference between sets is denoted by ‘A – B’, is the set containing elements of set A but not in B. i.e all elements of A except the element of B.

## Complement
Complement of a set A, denoted by

$A^\complement$

, is the set of all the elements except A. Complement of the set A is U – A.