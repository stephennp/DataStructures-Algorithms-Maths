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