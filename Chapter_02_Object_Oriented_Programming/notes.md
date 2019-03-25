#### 2.1 Goals, Principles, and Patterns
##### 2.1.3 Design Patterns
We present several design patterns in this book, and we show how they can be consistently applied to implementations of data structures and algorithms. These design patterns fall into **two groups—patterns** for solving algorithm design problems and patterns for solving software engineering problems.

The algorithm **design patterns** we discuss include the following:

* Recursion (Chapter 4)
* Amortization (Sections 5.3 and 11.4)
* Divide-and-conquer (Section 12.2.1)
* Prune-and-search, also known as decrease-and-conquer(Section 12.7.1) • Brute force (Section 13.2.1)
* Dynamic programming (Section 13.3).
* The greedy method (Sections 13.4.2, 14.6.2, and 14.7)

Likewise, the **software engineering** design patterns we discuss include:

* Iterator (Sections 1.8 and 2.3.4)
* Adapter (Section 6.1.2)
* Position (Sections 7.4 and 8.1.2)
* Composition (Sections 7.6.1, 9.2.1, and 10.1.4)
* Template method (Sections 2.4.3, 8.4.6, 10.1.3, 10.5.2, and 11.2.1) • Locator (Section 9.5.1)
* Factory method (Section 11.2.1)

#### 3.1 Experimental Studies
##### 3.1.1 Moving Beyond Experimental Analysis

Our goal is to develop an approach to analyzing the efficiency of algorithms that:
1. Allows us to evaluate the relative efficiency of any two algorithms in a way that is independent of the hardware and software environment.
2. Is performed by studying a high-level description of the algorithm without need for implementation.
3. Takes into account all possible inputs.

**primitive operations** such as the following:

* Assigning an identifier to an object
* Determining the object associated with an identifier
* Performing an arithmetic operation (for example, adding two numbers) • Comparing two numbers
* Accessing a single element of a Python list by index
* Calling a function (excluding operations executed within the function) • Returning from a function.

#### 3.2 The Seven Functions Used in This Book

**Proposition 3.1** *(Logarithm Rules) Given real numbers a > 0, b > 1, c > 0 and d > 1, we have:*

##### 1. The Constant Function

```math
f(n) = c
```

##### 2. The Logarithm Function

```math
1. \log_b(ac) = log_ba + log_bc

2. \log_b(a/c) = log_ba - log_bc

3. \log_b(a^c) = clog_ba

4. \log_ba = log_da / log_db

5. b^{\log_da} = a^{log_db}
```

##### 3. The Linear Function

```math
f(n) = n
```

##### 4. The N-Log-N Function

```math
f(n) = nlogn
```

##### 5. The Quadratic Function

```math
f(n) = n^2
```

##### 6. The Cubic Function

```math
f(n) = n^3
```

##### Polynomials
Most of the functions we have listed so far can each be viewed as being part of a larger class of functions, the **polynomials**. A polynomial function has the form,

```math
f(n) = a_0 +a_1n+a_2n^2 +a_3n^3 +···+a_dn^d
```

where `$a_0$`, `$a_1$` , . . . , `$a_d$` are constants, called the **coefficients** of the polynomial, and`$a_d \neq 0$`. Integer `d`, which indicates the highest power in the polynomial, is called the **degree** of the polynomial.

##### 7. The Exponential Function
**Proposition 3.4** *(Exponent Rules): Given positive integers a, b, and c, we have*
```math
1. (b^a)^c = b^{ac}

2. b^ab^c = b^{a+c}

3. b^a/b^c = b^{a-c}
```

`$b^{a/c} = (b^a)^{1/c}$` extended from Exponent rule 1.

`$b^d = 1/b^{-d}$` extended from Exponent rule 3

##### Geometric Sums
**Proposition 3.5**: *For any integer `$n ≥ 0$` and any real number `$a$` such that `$a > 0$` and `$a \neq 1$`, consider the summation*

```math
\sum_{i=0}^na^i = 1 + a + a^2 + \cdots + a^n
```

*(remembering that `$a^0 = 1$` if `$a > 0$`). This summation is equal to*

```math
\tfrac{a^{n+1}-1}{a-1}
```

##### 3.2.1 Comparing Growth Rates

##### floor function and ceiling function

`$\lfloor x \rfloor$` = the largest integer less than or equal to `$x$`.

`$\lceil x \rceil$` = the smallest integer greater than or equal to `$x$`.

##### 3.3.1 The “Big-Oh” Notation

Let `$f(n)$` and `$g(n)$` be functions mapping positive integers to positive real numbers. We say that `$f(n)$` is `$O(g(n))$` if there is a real constant `$c > 0$` and an integer constant `$n_0 ≥ 1$` such that

`$f(n) ≤ cg(n)$`, for `$n ≥ n_0$`.

This definition is often referred to as the “big-Oh” notation, for it is sometimes pro-
nounced as “`$f(n)$` is ***big-Oh*** of `$g(n)$`.”

It is considered poor taste to say “`$f(n) ≤ O(g(n))$`,” since the big-Oh already denotes the “less-than-or-equal-to” concept. Likewise, although common, it is not fully correct to say “`$f(n) = O(g(n))$`,” with the usual understanding of the “`$=$`” relation, because there is no way to make sense of the symmetric statement, “`$O(g(n)) = f(n)$`.” It is best to say,

“`$f(n)$` ***is*** `$O(g(n))$`.”

Alternatively, we can say “`$f(n)$` is ***order of*** `$g(n)$`.”

**Proposition 3.7** *The algorithm, find max, for computing the maximum element of a list of n numbers, runs in O(n) time.*

The initialization before the loop begins requires only a constant number of primitive operations. Each iteration of the loop also requires only a constant number of primitive operations, and the loop execute `$n$` times. Therefore, we account for the number of primitive operations being `$c' + c''x$` for appropriate constants `$c'$` and `$c''$` that reflect, respectively, the work performed during inialization and the loop body. Because each primitive operation runs in constant time, we have that the running time of algorithm `find_max` on an input of size `$n$` is at most a constant times `$n$`; that is, we conclude that the running time of algorithm find_max is `$O(n)$`.

##### Some Properties of the Big-Oh Notation

**Proposition 3.9**: *If f (n) is a polynomial of degree d, that is,*

```math
f(n) = a_0 +a_1n+···+a_dn^d,
```

*and `$ad > 0$`, then `$f(n)$` is `$O(nd)$`.*

**Justification**: Note that, for `$n ≥ 1$`, we have `$1 ≤ n ≤ n2 ≤ ··· ≤ n^d$`; hence,

```math
a_0+a_1n+a_2n^2 +···+a_dn^d ≤ (|a0|+|a1|+|a2|+···+|ad|)n^d
```

We show that `$f(n)$` is `$O(n^d)$` by defining `$c = |a_0|+|a_1|+···+|a_d|$` and `$n_0 = 1$`.

##### Characterizing Functions in Simplest Terms

##### Big-Omega

`$f(n) ≥ cg(n)$`, for `$n ≥ n_0$`

##### Big-Theat

`$c'g(n) ≤ f(n) ≤ c''g(n)$` for `$n ≥ n_0$`

##### 3.3.3 Examples of Algorithm Analysis

##### Constant-Time Operations

Therefore, we say that the expression data[j] is evaluated in `$O(1)$` time for a Python list.

##### Prefix Averages

The next problem we consider is computing what are known as ***prefix averages*** of a sequence of numbers. Namely, given a sequence `S` consisting of `n` numbers, we want to compute a sequence `A` such that `$A[j]$` is the average of elements `$S[0], ..., S[j]$`, for `$j = 0,..., n-1$`, that is,

```math
A[j] = \tfrac{\sum^j_{i=0}S[i]}{j+1}
```

##### Three-Way Set Disjointness

The ***three-way set disjointness*** problem is to determine if the intersection of the three sequences is empty, namely, that there is no element x such that `$x∈A, x∈B$`, and `$x∈C$`.

##### Element Uniqueness
A problem that is closely related to the three-way set disjointness problem is the ***element uniqueness problem***. In the former, we are given three collections and we presumed that there were no duplicates within a single collection. In the element uniqueness problem, we are given a single sequence `$S$` with `$n$` elements and asked whether all elements of that collection are distinct from each other.

##### Using Sorting as a Problem-Solving Tool

The built-in function, `sorted`. It guarantees a worst-case running time of `$O(nlogn)$`;

#### 3.4 Simple Justification Techniques

##### 3.4.1 By Example
***counterexample***

##### 3.4.2 The "Contra" Attack

***contrapositive***

***contradiction***

##### 3.4.3 Induction and Loop Invariants

##### Induction

**Proposition 3.20:** *Consider the Fibonacci function `$F(n)$`, which is defined such that `$F(1) = 1$`, `$F(2) = 2$`, and `$F(n) = F(n-2) + F(n-1)$` for `$n > 2$`. (See Section 1.8.) We claim that `$F(n) < 2n$`.*

**Justification:** We will show our claim is correct by induction.

***Basecases:*** `$(n≤2)$`.`$F(1)=1<2=2^1$` and`$F(2)=2<4=2^2$`.

***Induction step:*** `$(n > 2)$`. Suppose our claim is true for all `$n' < n$`. Consider `$F(n)$`. Since `$n > 2$`, `$F(n) = F(n-2) + F(n-1)$`. Moreover, since both `$n-2$` and `$n-1$` are less than `$n$`, we can apply the inductive assumption (sometimes called the “inductive hypothesis”) to imply that `$F(n) < 2^{n-2} + 2^{n-1}$`, since

```math
2^{n-2} + 2^{n-1} < 2^{n-1} + 2^{n-1} = 2\cdot2^{n-1} = 2^n
```

##### Loop Invariants
