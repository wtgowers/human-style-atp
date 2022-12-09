---
layout: page
title: A list of problems
description:
background: '/img/maths_background.png'
mathjax: true
--- 

The problems here are ones that we would eventually like to be able to solve fully automatically. In that respect, they vary considerably in their difficulty, so they are annotated in such a way that we can get a clearer idea of what we will need to do in order to have a realistic chance of solving which problems. Some of the problems also come with links to detailed discussions of how a program might be expected to solve them. The problems in this list are not stated formally, but it should be clear to an experienced mathematician what formal statement is intended in each case. Eventually we would like to create a useful set of benchmark problems against which we can measure our progress. We are not close to that yet: so far, the list is very preliminary.

<h3>Topological spaces.</h3>

A union of two compact sets is compact. <em>[Requires creating an open cover]</em>

A compact subset of a Hausdorff topological space is closed. <em>[Requires creating an open cover. A number of other difficulties, but they seem more technical than conceptual.]</em>

A continuous image of a compact set is compact. <em>[Requires creating an open cover]</em>

A closed subset of a compact set is compact. <em>[Requires creating an open cover]</em>

A composition of continuous functions is continuous. <em>[Very routine -- could be solved easily by ROBOT]</em>

$\overline{\overline{A}}=\overline{A}$ for every set $A$. <em>[Should be routine. Good test problem. Involves library reasoning.]</em>

If $f(\overline{A})\subset\overline{f(A)}$ for every $A$ then $f$ is continuous. <em>[Routine but a bit tricky. Good test problem. Involves library reasoning.]</em>

If $f$ is continuous then $f(\overline{A})\subset\overline{f(A)}$ for every $A$. <em>[Routine but a bit tricky. Good test problem.]</em>

If $f$ is continuous then for every neighbourhood $N$ of $f(x)$ there is a neighbourhood $M$ of $x$ such that $f(M)\subset N$. <em>[Should be routine. Good test problem.]</em>

If for every $x$ and for every neighbourhood $N$ of $f(x)$ there is a neighbourhood $M$ of $x$ such that $f(M)\subset N$, then $f$ is continuous. <em>[Should be routine. Good test problem.]</em>

A continuous bijection from a compact space to a Hausdorff space is a homeomorphism. <em>[Hard to do from first principles, but a good test of library-reasoning capabilities if the program is allowed to use facts such as that a continuous image of a compact set is compact or that a compact subset of a Hausdorff space is closed.]</em>

<h3>Metric spaces.</h3>

A metric space is Hausdorff. <em>[Requires building two open sets. Just beyond ROBOT's capabilities, so good target problem.]</em>

The intersection of two open sets is open. <em>[Routine -- could be solved by ROBOT]</em>

A union of open sets is open. <em>[Routine but requires splitting into cases, so a good test problem for technical reasons.]</em>

If f is continuous and $a_n\to a$ then $f(a_n)\to f(a)$ (where f is a function between metric spaces). <em>[Routine -- could be solved by ROBOT]</em>

If $f(a_n)\to f(a)$ whenever $a_n\to a$ then f is continuous. <em>[Requires building a sequence. Raises interesting issues. Good target problem.]</em>

If f is continuous and $U$ is open then $f^{-1}(U)$ is open. <em>[Routine -- could be solved by ROBOT]</em>

If $f^{-1}(U)$ is open whenever U is open then f is continuous. <em>[Requires creating an open set. Good target problem.]</em>

A uniform limit of continuous functions is continuous. <em>[Beyond what Robot could do, but should be feasible with a bit of help from subtasks and other ideas. An important target problem.]</em>

A sequence (in a metric space) has at most one limit. <em>[Requires choosing an $\epsilon$ to be half the distance between two putative distinct limits. Should be doable with metavariables, and otherwise straightforward, so good target problem.]</em>

A continuous function on a sequentially compact metric space is bounded. <em>[Requires creating a suitable sequence if the function isn't bounded. Raises interesting issues, so good target problem.]</em>

Every sequentially compact metric space is complete. <em>[Routine but slightly tricky, so good target problem.]</em>

A composition of continuous functions is continuous. <em>[Very routine -- I think ROBOT could do this easily.]</em>

Every closed set contains its limit points. <em>[Very routine -- I would expect ROBOT to be able to do this.]</em>

Every set that contains all its limit points is closed. <em>[Requires creating a sequence and use of the Archimedean axiom, so an interesting target problem.]</em>

If X is compact and $f:X\to X$ is a map such that $d(f(x),f(y)) < d(x,y)$ whenever $x\ne y,$ then $f$ has a fixed point. <em>[This has a short and natural proof, but you have to do the right thing at each stage. It would be wonderful if without cheating we could get a fully automatic program to solve this problem.]</em>

Open balls are open. <em>[This requires a slightly tricky choice for the radius of a ball around a point in the open ball. Should be OK with metavariables, but some technical issues concerning dependencies, so a good test problem to check that the program is good on how variables depend on each other.]</em>

An infinite sequentially compact metric space contains a sequence $(a_n)$ that converges to a limit $a$ such that every $a_n$ is distinct from $a$. <em>[The obvious proof needs an inductive construction that uses dependent choice. It also needs the observation that if no term in the original sequence appears infinitely many times, then the same is true of a subsequence, in which case we can throw away all terms that equal the limit.]</em>

<h3>Sets and functions.</h3>

$f^{-1}(A\cup B)\subset f^{-1}(A)\cup f^{-1}(B).$ <em>[Very routine. Should be easily solvable by ROBOT.]</em>

$f(f^{-1}(B))\subset B.$ <em>[Very routine. Should be easily solvable by ROBOT.]</em>

$A\subset f^{-1}(f(A)).$ <em>[Very routine. Should be easily solvable by ROBOT.]</em>

If $f$ is an injection, then $f(A\cap B)=f(A)\cap f(B)$. <em>[Easy, but good test problem to see whether a system can handle equality in a satisfactory way.]</em>

An injection from a non-empty set has a left inverse. <em>[Involves the tricky issue that the left inverse needs to be defined everywhere, even if lots of values don't matter. So a good test problem and possibly hard to solve without cheating.]</em>

A surjection has a right inverse. <em>[Uses choice, so opens up quite a big can of worms. But maybe useful for that reason, particularly if our focus is on "classical" proofs.]</em>

$A\cap(B\cup C)=(A\cap B)\cup(A\cap C)$. <em>[Requires splitting into cases, so good test problem for technical reasons.]</em>

$(A\cap B)^c=A^c\cup B^c$. <em>[Requires splitting into cases, so good test problem for technical reasons.]</em>

<h3>Finiteness, cardinality, and basic use of induction</h3>

If $A$ is a subset of $\{1,2,\dots,n\}$, then there exists $k$ and a bijection from $A$ to $\{1,2,\dots,k\}$. 

There is no infinite chain of subsets of $\{1,2,\dots,n\}$.

There is no injection from $\mathbb N$ to $\{1,2,\dots,n\}$.

Find a surjection from $\mathbb N$ to $\mathbb N^2$.

Every non-empty set of integers that is bounded above has a maximum.

<h3>Sequences and series.</h3>

A sequence that converges is bounded. <em>[Requires induction to prove that the maximum of a finite set exists, or else needs to notice that it has a finite set to which this result applies. The latter would be nice but it's not easy to see how the matching would work.]</em>

A sequence that is unbounded above has a subsequence that tends to infinity. <em>[Requires building a sequence. Involves induction. This would be quite an ambitious target, though the sort of problem we'll need a system to be able to solve easily if it's going to be able to do even moderately interesting constructions in analysis.]</em>

A sequence of non-negative real numbers that tends to zero has a subsequence that sums to at most 1. <em>[Involves some of the challenges of the previous problem, as well as that of coming up with the idea of getting the $k$th term of the subsequence to be at most $2^{-k}$ (or something similar).]</em>

The squeeze theorem: if $a_n\to a$ and $b_n\to a$ and $a_n\leq c_n\leq a_n$ for every $n$, then $c_n\to a$. <em>[A good test for a basic algorithm.]</em>

If $A$ is a non-empty set of real numbers that is bounded above, then there is a sequence $(a_n)$ such that $a_n\in A$ for every $n$, and $a_n\to\sup(A)$. <em>[Needs countable choice. Also needs the program to come up with a strategy for showing that $a_n\to\sup(A)$, such as ensuring that $a_n>\sup(A)-1/n$ for every $n$.]</em>

<h3>Groups.</h3>

Let $x$ and $y$ be invertible elements of a monoid. Prove that $xy$ is invertible. <em>[A good test of mixing an equality problem with very simple logic moves (such as creation of metavariables).]</em>

Lagrange's theorem. <em>[Probably hard for a fully automatic prover. But one could start with a motivated proof and take things from there.]</em>

The kernel of a homomorphism is a normal subgroup. <em>[Should be pretty easy.]</em>
  
A normal subgroup is the kernel of a homomorphism. <em>[A lot harder, as it involves constructing the quotient group.]</em>

If $ab=ac$ then $b=c$. <em>[A good test of subtasks.]</em>

If $a^2=e$ for every element $a$, then $G$ is Abelian. <em>[Another good test of subtasks, but also of mixing equality with logic.]</em>

$(ab)^{-1}=b^{-1}a^{-1}$. <em>[Another good subtasks exercise]</em>

A normal subgroup of a normal subgroup need not be normal. <em>[A good test for an existence solver.]</em>

A normal subgroup is a union of conjugacy classes. <em>[Should be easy.]</em>

Every finite group is a subgroup of some permutation group $S_n$. <em>[I would hope that this would be easy, but I'm not absolutely sure.]</em>

Two permutations are conjugate in $S_n$ if and only if they have the same cycle type. <em>[I would hope that the only if direction was easy. The if direction could be quite a bit more complicated.]</em>

$A_4$ has no subgroup of index 2. <em>[This needs quite a lot of library reasoning -- to spot that such a subgroup would have to be normal, to see then that it would have to be a union of conjugacy classes, and to work out that it's not possible to find conjugacy classes (including $\\\{e\\\}$) with sizes adding up to 6. Part of this would require showing that the 4-cycles form two conjugacy classes, each of size 3, unless this too could be appealed to as a library result.]</em>

The orbit-stabilizer theorem. <em>[This is a rather good example of a proof that is essentially routine but is found hard by beginners. So it would be a very good test problem for any algebraic reasoner.]</em>

<h3>Rings</h3>

Let $x$ be a nilpotent element of a commutative ring with identity. Prove that $1+x$ is a unit. <em>[This is an example of a problem that requires some computation. It is also challenging because with a bit of experience one "just knows the answer", so it raises questions such as how that background knowledge should be stored, and whether it is reasonable to expect a program to come up with the answer without having the background. (A possible approach: start by assuming that $x^2=0$ and build up from there. Another approach -- start doing polynomial long division, spot a pattern for how it is going to go, and observe that the process will terminate when you get to $x^n$. But how will something like that be implemented by an algorithm?)</em>

<h3>Fields</h3>

Using just the field axioms, prove that $0x=0$ for every $x$. <em>[Tricky for beginning undergraduates, so likely to be tricky for a non-cheating program.]</em>

Using just the field axioms, prove that $(-x)(-y)=xy$ for every $x$ and $y$. <em>[Similar.]</em>

Prove that $\mathbb Q(\sqrt 2)$ is a field. <em>[The question here is how a program would discover the trick of multiplying numerator and denominator by the conjugate of the denominator.]</em>

Prove that left distributivity implies right distributivity. <em>[This should be a fairly easy question for a subtasks-based algorithm.]</em>

Prove that if $xy=0$ then $x=0$ or $y=0$. <em>[The proof is easy, but this might be slightly tricky for a program, as it involves splitting into cases -- though the cases are obvious. Here I assume that it's allowed to use the result that anything multiplied by 0 gives 0.]</em>

Define $n.1$ inductively by $0.1=0$ and $(n+1).1=n.1 + 1$ (where $n\in\mathbb N$ and the 1 on the right-hand side of the multiplication is the multiplicative identity element of the field). Suppose that there is a positive integer $n$ such that $n.1=0$. Prove that $n.x=0$ for every element $x$ of the field (defined in a similar way). Prove also that the minimal such $n$ is a prime. <em>[It might be a little bit tricky even to formulate these problems in a nice way. The proofs could be quite hard given the inductive definitions of $n.1$ and $n.x$ and the fact that one has to mix elementary number theory with the algebra.]</em>

<h3>Enumerative combinatorics</h3>

<em>This whole area is well out of reach of the approaches we have developed so far, so seems ripe for exploration.</em>

Let $X$ be a set of size $m$ and let $Y$ be a set of size $n$. Prove that the number of functions from $X$ to $Y$ is $n^m$. <em>[This is a trivial problem for an experienced mathematician, but presents a challenge to a program, as a formal proof looks somewhat different from the kind of "for each $x\in X$ we have $n$ choices for $f(x)$" type argument we might be inclined to give in a human context. The problem is harder still if it simply asks how many functions there are from $X$ to $Y$.]</em> 

The number of subsets of size $m$ of a set of size $n$ is $n!/m!(n-m)!$. <em>[This could be a hard problem, as the idea is needed of doing a double count of the number of permutations instead of going directly for combinations.]</em>

<h3>Natural numbers and divisibility</h3>

The numbers 3, 5 and 7 are prime. Is there another triple of primes of the form $n, n+2, n+4$? <em>[It is not obvious how one could get a program to consider looking at the reduction mod 3, unless we slightly "cheated" and gave it a heuristic (of a kind that many humans use) that it is often a good idea to consider reductions to small moduli when solving simple number-theoretic problems. Even then one would want it to distinguish between problems for which the heuristic might be useful and problems for which it is obviously not useful at all.]</em>

Let $x$ and $y$ be positive integers with $x$ odd and $y$ even. Prove that $3x^2-4xy+2y^2\ne x^2$. <em>[The subtlety here is that the most natural proof uses two different heuristics for proving that a number are not equal. The first is to prove that one minus the other is strictly positive, and the second is to find some property, such as parity, that distinguishes between them. Here, if we subtract $x^2$ from both sides we find that it is enough to prove that $2(x-y)^2\ne 0$ and hence that $(x-y)^2\ne 0$, and hence that $x-y\ne 0$, and hence that $x\ne y$. For the last step we use the fact that $x$ is odd and $y$ is even. So this becomes a problem about how to choose appropriate heuristics.]</em>

Prove that there is exactly one prime $p$ such that $p^2+44$ is also prime. <em>[This is not a very hard problem, but the question is again how best to get the program to think of reducing mod 3.]</em>

Let $a_1=p$ be a prime and for each positive integer $n$ let $a_{n+1}=2a_n-1$. Prove that there exists $n$ such that $a_n$ is composite. <em>[There are various approaches to this, but they require enough of an idea that the problem is not quite routine, and it is therefore challenging to think how a program might solve it.]</em>

<h3>Rationality and irrationality</h3>

Prove that $\sqrt 3$ is irrational, having been shown a proof that $\sqrt 2$ is irrational. (This is not really about irrationality but about a very simple process of generalization and abstraction.)

Find two irrational numbers that add up to a rational number.

Prove that a rational number plus an irrational number is always irrational.

Prove that $\sqrt 2+\sqrt 3$ is irrational (given that $\sqrt n$ is irrational unless $n$ is a perfect square).
