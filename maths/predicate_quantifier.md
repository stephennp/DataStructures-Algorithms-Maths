# Intro
- Consider the following example. We need to convert the following sentence into a mathematical statement using propositional logic only.
  - `"Every person who is 18 years or older, is eligible to vote."`
- The above statement cannot be adequately expressed using only propositional logic. The problem in trying to do so is that propositional logic is not expressive enough to deal with quantified variables  
- . It would have been easier if the statement were referring to a specific person. But since it is not the case and the statement applies to all people who are 18 years or older, we are stuck.

## Predicate Logic (Logic thuộc tính)
- Predicate logic is an `extension of Propositional logic`.
- It adds the concept of predicates and quantifiers to better capture the meaning of statements that cannot be adequately expressed by propositional logic.
### 1. What is predicate logic or first order logic? (aka Function)
- Consider the statement, `x is greater than 3`. It has two parts:
  - The first part, the variable `x`, is the `subject` of the statement.
  - The second part, `is greater than 3`, is the `predicate`. It refers to a `property` that the subject of the statement can have.
- The statement `x is greater than 3` can be denoted by $P(x)$ where $P$ denotes the predicate `is greater than 3` and $x$ is the `variable`.
- The predicate P can be considered as a `function`. It tells the truth value of the statement $P(x)$ at $x$
- Once a value has been assigned to the variable `x`, the statement $P(x)$ becomes a proposition and has a truth or false(tf) value.
- In general, a statement involving n variables $x1, x2, x3,.. , xn$ can be denoted by $P(x1, x2, x3,.. , xn)$. Here P is also referred to as `n-place predicate` or a `n-ary predicate`.
- Example 1: Let $P(x)$ denote the statement `x > 10`.
  - What are the truth values of $P(11)$ and $P(5)$?
  - Solution: $P(11)$ is equivalent to the statement `11 > 10`, which is `True`.
  - $P(5)$ is equivalent to the statement `5 > 10`, which is `False`.
- Example 2: Let $R(x,y)$ denote the statement `x = y + 1`.
  - What is the truth value of the propositions `R(1,3)` and `R(2,1)`?
  - Solution: `R(1,3)` is the statement `1 = 3 + 1`, which is `False`.
  - `R(2,1)` is the statement `2 = 1 + 1`, which is `True`.

## Quantifier logic ( logic định lượng)
- In predicate logic, predicates are used alongside quantifiers to express the extent to which a predicate is `true` over a `range of elements`.
- Using `quantifiers` to create such propositions is called quantification.
### 1. Universal Quantification (aka For All)
- Mathematical statements sometimes assert that a property is true for all the values of a variable in a particular domain, called the domain of discourse. Such a statement is expressed using universal quantification.
- The universal quantification of $P(x)$ for a particular domain is the proposition that asserts that $P(x)$ is true for all values of $x$ in this domain
- The domain is very important here since it decides the possible values of `x`
- The meaning of the universal quantification of P(x) changes when the domain is changed. The domain must be specified when a universal quantification is used, as without it, it has no meaning.
- Formally,
  - The universal quantification of P(x) is the statement
`P(x) for all values of x in the domain`
  - The notation $\forall P(x)$ denotes the universal quantification of $P(x)$.
  - Here $\forall$ is called the universal quantifier.
$\forall P(x)$ is read as `for all x P(x)`. 
- Example 1:
  - Let $P(x)$ be the statement `x + 2  > x`.
  - What is the truth value of the statement $\forall xP(x)$?
  - Solution: As `x+2` is greater than `x` for any real number, so $P(x) \equiv T$ for all x or $\forall xP(x) \equiv T$.
### 2. Existential Quatification (aka For exist at least one)
- Some mathematical statements assert that there is an element with a certain property.
- Such statements are expressed by existential quantification
- Existential quantification can be used to form a proposition that is `true if and only if P(x) is true` for at `least` one value of `x` in the domain.
- Formally
  - The existential quantification of $P(x)$ is the statement
`There exists an element x in the domain such that P(x)`
- The notation $\exists P(x)$ denotes the existential quantification of $P(x)$.
Here $\exists$ is called the `existential quantifier`. 
$\exists P(x)$ is read as `There is at least one such x such that P(x)`. 

### 3.  Uniqueness quantifier
- Denoted by $\exists !$.
- The notation $\exists !xP(x)$ states `There exists a unique x such that P(x) is true`.

### 4. Quantifiers with restricted domains
- As we know that quantifiers are `meaningless` if the variables they bind `do not` have a `domain`.
- The following abbreviated notation is used to restrict the domain of the variables $\forall x > 0, x^2 > 0$.
- The above statement restricts the domain of x, and is a shorthand for writing another proposition, that says `x > 0`, in the statement.
- If we try to rewrite this statement using an implication, we would get-
$\forall x (x > 0\: \rightarrow \: x^2 > 0)$
- Similarly, a statement using Existential quantifier can be restated using conjunction between the domain restricting proposition and the actual predicate.
  - Restriction of universal quantification is the same as the universal quantification of a conditional statement.
  - Restriction of an existential quantification is the same as the existential quantification of conjunction.

## Summary

  | Statement      | When `true`?        | When `false` |
  |----------------|----------------------|------------|
  | $\forall P(x)$       | $P(x)$ is `true` for all `x`       | There is an `x` Which $P(x)$ is `false` |
  | $\exists P(x)$       | There is an `x` Which $P(x)$ is `true`       | $P(x)$ is `false` for all `x` |

- Now if we try to convert the statement, given in the beginning of this article, into a mathematical statement using predicate logic, we would get something like-
$\forall P(x) \leftrightarrow Q(x)$
  - Here, $P(x)$ is the statement `x is 18 years or older and`
  - $Q(x)$ is the statement `x is eligible to vote`.
- Notice that the given statement is not mentioned as a biconditional and yet we used one. This is because Natural language is ambiguous sometimes, and we made an assumption. This assumption was made since it is true that a person can vote `if and only if he/she is 18 years or older`

## Definitions to Note:
1. `Binding variables`
  - A variable whose occurrence is bound by a quantifier is called
a `bound variable`.
  - Variables not bound by any quantifiers are called `free variables`.
2. `Scope` - The part of the logical expression to which a quantifier is applied is called
the scope of the quantifier.

## Logical Equivalences involving Quantifiers
- Two logical statements involving predicates and quantifiers are considered equivalent if and only if they have the same truth value no matter which predicates are substituted into these statements irrespective of the domain used for the variables in the propositions.
- There are two very important equivalences involving quantifiers, given below:
  1.  $\forall x(P(x)\wedge Q(x)) \equiv \forall xP(x) \wedge \forall xQ(x)$

  2.  $\exists x(P(x)\vee Q(x)) \equiv \exists xP(x) \vee \exists xQ(x)$
- $P\Leftrightarrow Q$, which can also be restated as $P\Rightarrow Q \wedge Q\Rightarrow P$.
- If they are equivalent then
  - $\forall x(P(x)\vee Q(x)) \Leftrightarrow \forall xP(x) \vee \forall xQ(x)$ and,
  - $\exists x(P(x)\wedge Q(x)) \Leftrightarrow \exists xP(x) \wedge \exists xQ(x)$ both must be true.

- Let us first check for $\forall x(P(x)\vee Q(x)) \Leftrightarrow \forall xP(x) \vee \forall xQ(x)$.
  - Is $\forall x(P(x)\vee Q(x)) \Rightarrow \forall xP(x) \vee \forall xQ(x)$ true? `No`.
  - `Proof` – Suppose that the Hypothesis $\forall x(P(x)\vee Q(x))$ is true. That means there are certain `x` for which $P(x)$ is true and others where $Q(x)$ is true.
  - It is also possible that for some `x` both $P(x)$ and $Q(x)$ are true. But in any case, all `x` must either satisfy $P(x)$ or $Q(x)$ or both, since the hypothesis is true.
  - The conclusion(RHS) is true when the `disjunction` is true. As is clear from the above reasoning that P`(x)` is true for some values of x and Q(x) for some.
  - Thus both $\forall xP(x)$ and $\forall xQ(x)$ are `false`, since neither of them are true for all values of x.
  - In the case where $P(x)$ and $Q(x)$ hold for all x then this equivalence is true, but otherwise it is false.

  - So, $\forall xP(x) \vee \forall xQ(x) \equiv F$. According to our assumption, the hypothesis is true, but our conclusion turned out to be false. This cannot be true for a conditional, therefore the conditional
$\forall x(P(x)\vee Q(x)) \Rightarrow \forall xP(x) \vee \forall xQ(x)$ is false.
- Since one conditional is false, the complete biconditional is false.
Hence, $\forall x(P(x)\vee Q(x)) \not\equiv \forall xP(x) \vee \forall xQ(x)$.
- In a similar way, it can also be proved that,
$\exists x(P(x)\wedge Q(x)) \not\equiv \exists xP(x) \wedge \exists xQ(x)$

### Negating Quantified statements
- Consider the statement `Every Computer Science Graduate has taken a course in Discrete Mathematics`
- The above statement is a universal quantification, $xP(x)$
where $P(x)$ is the statement `x has taken a course in Discrete Mathematics` and the domain of `x` is all Computer Science Graduates.
- The negation of this statement is `It is not the case that every computer science graduate has taken a course in Discrete Mathematics` or simply `There is a computer science graduate who has not taken a course in Discrete Mathematics`.
- The above statement can be expressed using an existential quantification.
$\exists x \neg P(x)$
- Thus, we get the following logical equivalence-
$\neg \forall xP(x) \equiv \exists x \neg P(x)$
- These equivalences are nothing but rules for negations of quantifiers. They are also known as `De Morgans’s laws` for quantifiers.

  | Statement      | Equivalent statement |  When `true`?        | When `false` |
  |----------------|----------|----------------------|------------|
  | $\neg \exists x P(x)$  |  $\forall  x \neg P(x)$   | $P(x) \equiv F$  for all `x`   | $P(x) \equiv T$  for some `x` |
  | $\neg \forall xP(x)$  |  $\exists x \neg P(x$   | $\neg P(x) \equiv T$  for all `x`      |  $P(x) \equiv T$  for some `x` |

### Nested Quantifiers
- It is possible to use two quantifiers such that one quantifier is within the scope of the other one. In such cases the quantifiers are said to be nested.
- For example, $\forall x \exists y (x + y = 0)$
- The above statement is read as `For all x, there exists a y such that x +  y = 0`.

 | Statement      | When `true`?        | When `false` |
  |----------------|----------|----------------------|------------|
  | $\forall x \forall y P(x,y)$ <br> $\forall y \forall x P(x,y)$ |  $P(x,y) \equiv T$  for every `(x,y)`   | $P(x,y) \equiv F$  for some `x` |
  | $\forall x \exists y P(x,y)$  |  For every x there is a y such that $P(x,y) \equiv T$   | There is an x such that $P(x,y) \equiv F$ for all y |
  | $\exists x \forall y P(x,y)$  |  There is an x such that $P(x,y) \equiv T$ for all y  | For every x there is a y such that $P(x,y) \equiv F$ |
   | $\exists x \exists y P(x,y)$ <br> $\exists y \exists x P(x,y)$ |  $P(x,y) \equiv T$  for some `(x,y)`   | $P(x,y) \equiv F$  for all `(x,y)` |