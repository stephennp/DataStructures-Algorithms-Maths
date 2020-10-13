# Intro
This topic will help to understand basic mathematics for programmers

## Propositional Logic (Logic Mệnh đề)
- Logic is the basis of all mathematical reasoning  and of all automated reasoning
  - $\exists x$  such that $x \neq a^2 +b^2$, where $a,b,c \in Z$
- Importance of Mathematical Logic
  - The rules of logic give precise meaning to mathematical statements
  - These rules are used to distinguish between valid and invalid mathematical arguments.
- `What is a proposition?`
  - A proposition is the basic building block of logic
  - It is defined as a declarative sentence that is either **True or False, but not both**.
  - The **Truth Value** of a proposition is True(denoted as T) if it is a true statement, and False(denoted as F) if it is a false statement.
  - For examples `valid` propositions
    1. The sun rises in the East and sets in the West.
    2. 1 + 1 = 2
    3. 'b' is a vowel.
    - All of the above sentences are propositions, where the first two are Valid(True) and the third one is Invalid(False).
    - Some sentences that do not have a truth value or may have **more** than one truth value are not propositions.
  - For examples `invalid` propositions
    1. What time is it?
    2. Go out and play.
    3. x + 1 = 2.
    - The first two do not have a truth value, and the third one may be true or false.
  - Propositional variables: $p, q, r s$
  - The area of logic which deals with propositions is called `propositional calculus` or `propositional logic`
  - It also includes producing new propositions using existing ones.
  - Propositions constructed using one or more propositions are called `compound propositions`.
  - The propositions are combined together using `Logical Connectives` or `Logical Operators`. (biểu thức mệnh đề)

## Truth table

### 1. Negation (aka !)
- If $P$ is a proposition, then the negation of $P$  is denoted by $\neg P$, which when translated to simple English means- “It is not the case that $P$” or simply “not $P$“.
- The truth value of $\neg P$ is the opposite of the truth value of $P$.
- Example:
  The negation of `It is raining today`, is `It is not the case that is raining today` or simply `It is not raining today`.

### 2. Conjunction (aka &)
- For any two propositions p and q, their conjunction is denoted by $p\wedge q$, which means `p and q`.
- The conjuction $p\wedge q$ is **True** when both `p and q are True`, otherwise False.
- The truth table of $p\wedge q$ is:

  | p | q | $p\wedge q$ |
  |---|---|-----|
  | T | T | T   |
  | T | F | F   |
  | F | T | F   |
  | F | F | F   |
- Example:
  - The conjunction of the propositions p – `Today is Friday` and q – `It is raining today`, $p\wedge q$ is `Today is Friday and it is raining today`. This proposition is true only on rainy Fridays and is false on any other rainy day or on Fridays when it does not rain.

### 3. Disjuntion (aka ||)

For any two propositions p and q, their disjunction is denoted by $p\vee q$, which means `p or q`. The disjuction p\vee q is True when either p or q is True, otherwise False.
The truth table of $p\vee q$ is-

  | p | q | $p\vee q$ |
  |---|---|-----|
  | T | T | T   |
  | T | F | T   |
  | F | T | T   |
  | F | F | F   |
- Example:
  - The disjunction of the propositions p – `Today is Friday` and q – `It is raining today`, $p\vee q$ is `Today is Friday or it is raining today`.
  - This proposition is `true` on any day that is a Friday or a rainy day(including rainy Fridays) and is false on any day other than Friday when it also does not rain.

### 4. Exclusive Or (aka NOR)
- For any two propositions p and q, their `exclusive or` is denoted by $p\oplus q$, which means `either p or q but not both`.
- The exclusive or $p\oplus q$ is True when either p or q is True, and False when both are true or both are false.
The truth table of $p\oplus q$ is-

  | p | q | $p\oplus q$ |
  |---|---|-----|
  | T | T | F   |
  | T | F | T   |
  | F | T | T   |
  | F | F | F   |

- Example:
  - The exclusive or of the propositions p – `Today is Friday` and q – `It is raining today`, $p\oplus q$ is `Either today is Friday or it is raining today, but not both`.
  - This proposition is `true` on any day that is a Friday or a rainy day(not including rainy Fridays) and is `false` on any day other than Friday when it does not rain or rainy Fridays.

### 5. Implication (aka If)
- For any two propositions p and q, the statement `if p then q` is called an implication and it is denoted by $p\rightarrow q$.
- In the implication $p\rightarrow q$, p is called the `hypothesis` or `antecedent` or `premise` and q is called the `conclusion or consequence`.
- The implication is `p\rightarrow q` is also called a `conditional statement`.
- The implication is false when p is true and q is false otherwise it is true. The truth table of $p\rightarrow q$ is-

  | p | q | $p\rightarrow q$ |
  |---|---|-----|
  | T | T | T   |
  | T | F | F   |
  | F | T | T   |
  | F | F | T   |

- Example,
  - `If it is Friday then it is raining today` is a proposition which is of the form $p\rightarrow q$.
  - The above proposition is true if it is not Friday(premise is false) or if it is Friday and it is raining, and it is false when it is Friday but it is not raining.

### 6. Biconditional or Double Implication
-  For any two propositions p and q, the statement “p if and only if(iff) q” is called a biconditional and it is denoted by $p\leftrightarrow q$.
- The statement $p\leftrightarrow q$ is also called a bi-implication.
-  $p\leftrightarrow q$ has the same truth value as ($p\rightarrow q$) $\land$ ($q\rightarrow p$)
- The implication is `true` when `p and q have same truth values`, and is `false` otherwise. The truth table of $p\leftrightarrow q$ is-

  | p | q | $p\leftrightarrow q$ |
  |---|---|-----|
  | T | T | T   |
  | T | F | F   |
  | F | T | F   |
  | F | F | T   |
- Example:
  - `It is raining today if and only if it is Friday today.` is a proposition which is of the form $p\leftrightarrow q$.
  - The above proposition is `true` if it is not Friday and it is not raining or if it is Friday and it is raining, and it is `false` when it is not Friday or it is not raining.

### 7. De Morgan’s Law
 - In propositional logic and boolean algebra, De Morgan’s laws are a pair of transformation rules that are both valid `rules of inference`
 - In formal language, the rules are written as: 
    - $\lnot (p \land q) \equiv \lnot p \lor \lnot q$
    - $\lnot (p \lor q) \equiv \lnot p \land \lnot q$
- Proof by Truth Table

  | p | q | $\lnot p$ | $\lnot q$ | $p \land q$ | $\lnot p \lor \lnot q$ | $p \lor q$ | $\lnot p \land \lnot q$ |
  |---|---|-----------|-----------|-------------|------------------------|------------|-------------------------|
  | T | T | F         | F         | T           | F                      | T          | F                       |
  | T | F | F         | T         | F           | T                      | T          | F                       |
  | F | T | T         | F         | F           | T                      | T          | F                       |
  | F | F | T         | T         | F           | T                      | F          | T                       |

- There are three related conditional statements that occur so often that they have special names
    - Implication : $p\rightarrow q$
    - Converse : The converse of the proposition $p\rightarrow q$ is $q\rightarrow p$
    - Contrapositive : The contrapositive of the proposition $p\rightarrow q$ is $\neg q\rightarrow \neg p$
    - Inverse : The inverse of the proposition $p\rightarrow q$ is $\neg p\rightarrow \neg q$
- To summarise:
  | Statement      | If p, then q         |
  |----------------|----------------------|
  | Converse       | If q, then p         |
  | Contrapositive | If not q, then not p |
  | Inverse        | If not p, then not q |

- **Note** :
  - It is interesting to note that the truth value of the conditional statement $p\rightarrow q$ is the same as it’s `contrapositive`
  - The truth value of the Converse of $p\rightarrow q$ is the same as the truth value of its Inverse.
  - When two compound propositions always have the same truth value, they are said to be equivalent.
    - Therefore:
    - $p \rightarrow q \equiv \neg q \rightarrow \neg p$
    - $q \rightarrow p \equiv \neg p \rightarrow \neg q$

  | p | q | $\lnot p$ | $\lnot q$ | $p \rightarrow q$ | $\lnot p \rightarrow \lnot q$ | $q \rightarrow p$ | $\lnot q \rightarrow \lnot p$ |
  |---|---|-----------|-----------|-------------|------------------------|------------|-------------------------|
  | T | T | F         | F         | T           | T                      | T          | T                       |
  | T | F | F         | T         | F           | F                      | T          | T                       |
  | F | T | T         | F         | T           | T                      | F          | F                       |
  | F | F | T         | T         | T           | T                      | T          | T                       |

- Example:
  - Implication : If today is Friday, then it is raining.
  - The given proposition is of the form p\rightarrow q, where p is “Today is Friday” and q is “It is raining today”. Contrapositive, Converse, and Inverse of the given proposition respectively are-
    - **Converse** : If it is raining, then today is Friday
    - **Contrapositive** :If it is not raining, then today is not Friday
    - **Inverse** : If today is not Friday, then it is not raining