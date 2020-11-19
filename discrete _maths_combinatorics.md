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
  - `Solution` – Let N_1, N_2, and N_3 denote the number of possible variable names of length 1, 2, and 3. Therefore, total number of variable names is N_1 + N_2 + N_3.
    For N_1 there are only 52 possibilities since the first character has to be an alphabet.
    For N_2, there are 52 _ 62 = 3224 possibilities
    For N_3, there are 52 _ 62 \* 62 = 199888 possibilities
    Therefore, total number of variable names = 52 + 3224 + 199888 = 203164
