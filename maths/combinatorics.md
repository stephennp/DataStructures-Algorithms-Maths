# Intro

## The Pigeonhole Principle

- Suppose that a flock of 20 pigeons flies into a set of 19 pigeonholes to roost.
- Because there are 20 pigeons but only 19 pigeonholes, a least one of these 19 pigeonholes must have at least two pigeons in it.
- To see why this is true, note that if each pigeonhole had at most one pigeon in it, at most 19 pigeons, one per hole, could be accommodated
- This illustrates a general principle called the pigeonhole principle, which states that if there are more pigeons than pigeonholes, then there must be at least one pigeonhole with at least two pigeons in it.

## Theorem

1. If “A” is the average number of pigeons per hole, where A is not an integer then

   - At least one pigeon hole contains ceil[A] (smallest integer greater than or equal to A) pigeons
   - Remaining pigeon holes contains at most floor[A] (largest integer less than or equal to A) pigeons

2. We can say as, if n + 1 objects are put into n boxes, then at least one box contains two or more objects.
   The abstract formulation of the principle: Let X and Y be finite sets and let $f:A\rightarrow B$ be a function.

   - If X has more elements than Y, then f is not one-to-one.
   - If X and Y have the same number of elements and f is onto, then f is one-to-one.
   - If X and Y have the same number of elements and f is one-to-one, then f is onto.

## Pigeonhole principle strong form

- `Theorem`: Let q1, q2, . . . , qn be positive integers.
- If `q1+ q2+ . . . + qn – n + 1` objects are put into n boxes, then either the 1st box contains at least q1 objects, or the 2nd box contains at least q2 objects, . . ., the nth box contains at least qn objects.
- Application of this theorem is more important, so let us see how we apply this theorem in problem solving.
- `Example – 1`: In a computer science department, a student club can be formed with either 10 members from first year or 8 members from second year or 6 from third year or 4 from final year. What is the minimum no. of students we have to choose randomly from department to ensure that a student club is formed?
  - `Solution`: we can directly apply from the above formula where,
    q1 =10, q2 =8, q3 =6, q4 =4 and n=4
  - Therefore the minimum number of students required to ensure department club to be formed is
    `10 + 8 + 6 + 4 – 4 + 1 = 25`
- `Example – 2`: A box contains 6 red, 8 green, 10 blue, 12 yellow and 15 white balls. What is the minimum no. of balls we have to choose randomly from the box to ensure that we get 9 balls of same color?
  - `Solution`: Here in this we cannot blindly apply pigeon principle. First we will see what happens if we apply above formula directly.
  - From the above formula we have get answer 47 because 6 + 8 + 10 + 12 + 15- 5 + 1 = 47
    But it is not correct. In order to get the correct answer we need to include only blue, yellow and white balls because red and green balls are less than 9. But we are picking randomly so we include after we apply pigeon principle.
    i.e., 9 blue + 9 yellow + 9 white – 3 + 1 = 25
  - Since we are picking randomly so we can get all the red and green balls before the above 25 balls. Therefore we add 6 red + 8 green + 25 = 39
  - We can conclude that in order to pick 9 balls of same color randomly, one has to pick 39 balls from a box.

## Combinatorics

- is the branch of Mathematics dealing with the study of finite or countable discrete structures. - It includes the enumeration or counting of objects having certain properties. Counting helps us solve several types of problems such as counting the number of available IPv4 or IPv6 addresses.

## Counting Principles

- There are two basic counting principles, sum rule and product rule.
- `Sum Rule` – If a task can be done in one of $n_1$ ways or one of $n_2$ ways, where none of the set of $n_1$ ways is the same as any of the set of $n_2$ ways, then there are $n_1$ + $n_2$ ways to do the task.
- `Product Rule` – If a task can be broken down into a sequence of `k` subtasks, where each subtask can be performed in $n_1, n_2,.. n_k$ respectively, then the total number of ways the task can be performed is $n_1 * n_2 * ... * n_k$.

- Examples:
- Example 1 – In how many ways can 3 winning prizes be given to the top 3 players in a game played by 12 players?
  - `Solution` – We have to distribute 3 prizes among 12 players. This task can be divided into 3 subtasks of assigning a single prize to a certain player.
    Giving out the first prize can be done in 12 different ways. After giving out the first prize, two prizes remain and 11 players remain. Similarly, the second prize and third prize can be given in 11 ways and 10 ways. The total number of ways by the product rule is 12 _ 11 _ 10 = 1320.
- Example 2 – In how many ways can a person choose a project from three lists of projects of sizes 10, 15, and 19 respectively?
  - `Solution` – The person has a choice of choosing a project from either of the three lists. So the person can choose from either 10 projects or 15 projects or 19 projects. Since choosing from one list is not the same as choosing another list, the total number of ways of choosing a project by the sum-rule is 10 + 15 + 19 = 44.
- Example 3 – How many distinct license plates are possible in the given format- Two alphabets in uppercase, followed by two digits then a hyphen and finally four digits. Sample- AB12-3456.
  - `Solution` – There are 26 possibilities for the each of the two letters and 10 possiblities for each of the digits. Therefore the total number of possibilities is – 26 _ 26 _ 10 _ 10 _ 10 _ 10 _ 10 \* 10 = 676000000.
- Example 4 – How many variable names of length upto 3 exist if the variable names are alphanumeric and case sensitive with the restriction that the first character has to be an alphabet?
  - `Solution` – Let N*1, N_2, and N_3 denote the number of possible variable names of length 1, 2, and 3. Therefore, total number of variable names is N_1 + N_2 + N_3.
    For N_1 there are only 52 possibilities since the first character has to be an alphabet.
    For N_2, there are 52 * 62 = 3224 possibilities
    For N*3, there are 52 * 62 \* 62 = 199888 possibilities
    Therefore, total number of variable names = 52 + 3224 + 199888 = 203164

## Principle of Inclusion-Exclusion

- The sum-rule mentioned above states that if there are multiple sets of ways of doing a task, there shouldn’t be any way that is common between two sets of ways because if there is, it would be counted twice and the enumeration would be wrong.
- The principle of inclusion-exclusion says that in order to count only unique ways of doing a task, we must add the number of ways to do it in one way and the number of ways to do it in another and then subtract the number of ways to do the task that are common to both sets of ways.
  The principle of inclusion-exclusion is also known as the subtraction principle. For two sets of ways $A_1$ and $A_2$, the enumeration would like-
- $|A_1 \cup A_2| = |A_1| + |A_2| - |A_1\cap A_2|$
- Example 1 – How many binary strings of length 8 either start with a ‘1’ bit `or` end with two bits ’00’?
  - Solution – If the string starts with one, there are 7 characters left which can be filled in 2^7 = 128 ways.
    - If the string ends with ’00’ then 6 characters can be filled in 2^6 = 64 ways.
    Now if we add the above sets of ways and conclude that it is the final answer, then it would be wrong. This is because there are strings with start with ‘1’ and end with ’00’ both, and since they satisfy both criteria they are counted twice.
    - So we need to subtract such strings to get a correct count.
    - Strings that start with ‘1’ and end with ’00’ have five characters that can be filled in 2^5 = 32 ways.
    - So by the inclusion-exclusion principle we get-
    - Total strings = 128 + 64 – 32 = 160
- Example 2 – How many numbers between 1 and 1000, including both, are divisible by 3 or 4?
  - Solution – Number of numbers divisible by 3 = $|A_1| =\lfloor 1000/3\rfloor$ = 333.
    - Number of numbers divisible by 4 = $|A_2| = \lfloor 1000/4\rfloor$ = 250.
    - Number of numbers divisible by 3 and 4 = $|A_1 \cap A_2| = \lfloor 1000/12\rfloor$ = 83.
    - Therefore, number of numbers divisible by 3 or 4 = $|A_1 \cup A_2|$ = 333 + 250 – 83 = 500

## PnC and Binomial Coefficients
- Several Counting problems require finding the number of ways to arrange a certain number of distinct elements, where the relative order of these elements matter, other problems focus on finding the number of ways of selecting a particular number of elements from a set, where the order of the elements does not matter.
- Both types of problems are similar except for one crucial difference, that difference is order.
### Permutation –
A permutation of a set of distinct objects is an ordered arrangement of these objects. A permutation is often also referred to as an arrangement. The relative order of the elements matters in an arrangement.
An ordered arrangement of r elements of a set is called an r-permutation. It is represented as P(n,r).
For $1\leq r\leq n$,
-  $\begin{flalign*} P(n,r) &= n * (n-1) * ... * (n-r+1)\\ &= \frac{n * (n-1) * ... * (n-r+1) * (n-r) *...* 2 * 1}{(n-r) * (n-r-1) * .... * 2 * 1}\\ &= \frac{n!}{(n-r)!} \end{flalign*} $

The above formula for $P(n,r)$ is a simple application of the product-rule.

- Example 1 – How many permutations of the string “ABCDEFGH” have the string “ABC” as a substring?
  - Solution
    - For “ABC” to be a substring, the letters A,B, and C must occur as a block. If we consider that block and the remaining 5 letters as objects, we have a total of 6 objects to arrange.
    - Therefore the number of strings having “ABC” as their substring = 6! = 720.
- Example 2 – Find the number of permutations of the word “CIVILIZATION”.
  - Solution – The word civilization has the following character frequency-
    ‘C’ – 1
    ‘I’ – 4
    ‘V’ – 1
    ‘L’ – 1
    ‘Z’ – 1
    ‘A’ – 1
    ‘T’ – 1
    ‘O’ – 1
    ‘N’ – 1
  - If all the characters were distinct, the number of permutations would be P(n,n) = n! where n = 12. But since the letter ‘I’ repeats 4 times, the number of permutations are less. This is because the permuation as a whole does not change if the ‘I’s’ are arranged amongst themselves. So to correct the number of permutations, we divide the total permutations by P(r,r) where r is the number of times a letter or object is repeated.
  - Total number of arrangements = $\frac{P(12,12)}{P(4,4)}$ = $\frac{12!}{4!}$ =  19958400

### Combination
- A combination of a set of distinct objects is just a count of the number of ways a specific number of elements can be selected from a set of a certain size. The order of elements does not matter in a combination.
- An unordered selection of r elements from a set is called an r-combination. It is represented as C(n,r) and $\binom{n}{r}$.
Since a combination is just a permutation without order, the number of r-combination can be expressed in terms of r-permutation.
The r-permutation can be obtained by first obtaining the r-combination and then ordering the elements in each r-combination, which can be done in P(r, r) ways.
 $\therefore P(n,r) = C(n,r) * P(r,r)\\$
 which gives us-

  $\begin{flalign*} C(n,r) &= \frac{P(n,r)}{P(r,r)}\\ &= \frac{n!}{(n-r)!} * \frac{1}{r!}\\ &= \frac{n!}{r!(n-r)!}& \end{flalign*}$

- Example 1 – Determine the number of ways in which 5 cards can be chosen from a deck of 52 cards, such that there is exactly one ace.
  - Solution – Out of the 4 aces, one can be chosen in \binom{4}{1} = 4 ways.
  - The remaining 4 cards have to be chosen from the remaining 48 cards. Number of ways of choosing these 4 cards is \binom{48}{4} = 194580.
  - Total number of ways of choosing 5 cards by product rule = \binom{4}{1} * \binom{48}{4} = 4 * 194580 = 778320.    

##  Distinguishable balls and Distinguishable boxes –

- With Exclusion – In case of exclusion, distribution is the same as counting r-permutations, as there are n choices for the first ball, n-1 for the second and so on.
- Without Exclusion – When the distribution is without exclusion, i.e. there is no restriction on the minimum number of balls a box has to have, the number of ways – n^m. This is because every ball has n choices.
- Fixed number of balls – If the distribution is such that each box should only have a fixed number of balls then the number of ways is-
\frac{m!}{m_1!m_2!...m_k!} where m_k is the number of balls to be put in the k^{th} box.

- Example 1 – In how many ways can 10 prizes be distributed among 5 people without exclusion?
- Solution – This situation is analogous to distributing distinct balls into distinct boxes without exclusion. For every prize there are 5 choices of people who can receive it. So the number of ways of distributing the prizes is- 5^{10}.