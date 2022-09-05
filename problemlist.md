---
layout: page
title: A list of problems
description:
background: '/img/maths_background.png'
mathjax: true
--- 

The problems here are ones that we would eventually like to be able to solve fully automatically. In that respect, they vary considerably in their difficulty, so they are annotated in such a way that we can get a clearer idea of what we will need to do in order to have a realistic chance of solving which problems. Some of the problems also come with links to detailed discussions of how a program might be expected to solve them. The problems in this list are not stated formally, but it should be clear to an experienced mathematician what formal statement is intended in each case.

<h3>Topological spaces.</h3>

A union of two compact sets is compact.

A compact subset of a Hausdorff topological space is closed.

A continuous image of a compact set is compact.

A closed subset of a compact set is compact.

A composition of continuous functions is continuous.

$\overline{\overline{A}}=\overline{A}$ for every set $A$.

If $f(\overline{A})\subset\overline{f(A)}$ for every $A$ then $f$ is continuous.

If $f$ is continuous then $f(\overline{A})\subset\overline{f(A)}$ for every $A$.

If $f$ is continuous then for every neighbourhood $N$ of $f(x)$ there is a neighbourhood $M$ of $x$ such that $f(M)\subset N$.

If for every $x$ and for every neighbourhood $N$ of $f(x)$ there is a neighbourhood $M$ of $x$ such that $f(M)\subset N$, then $f$ is continuous.

<h3>Metric spaces.</h3>

A metric space is Hausdorff.

The intersection of two open sets is open.

A union of open sets is open.

If f is continuous and $a_n\to a$ then $f(a_n)\to f(a)$ (where f is a function between metric spaces).

If $f(a_n)\to f(a)$ whenever $a_n\to a$ then f is continuous.

If f is continuous and $U$ is open then $f^{-1}(U)$ is open.

If $f^{-1}(U)$ is open whenever U is open then f is continuous.

A uniform limit of continuous functions is continuous.

A sequence (in a metric space) has at most one limit.

A continuous function on a sequentially compact metric space is bounded.

Every sequentially compact metric space is complete.

A composition of continuous functions is continuous.

Every closed set contains its limit points.

Every set that contains all its limit points is closed.

If X is compact and $f:X\to X$ is a map such that $d(f(x),f(y)) < d(x,y)$ whenever $x\ne y,$ then $f$ has a fixed point.

Open balls are open.

<h3>Sets and functions.</h3>

$f^{-1}(A\cup B)\subset f^{-1}(A)\cup f^{-1}(B).$

$f(f^{-1}(B))\subset B.$

$A\subset f^{-1}(f(A)).$

If $f$ is an injection, then $f(A\cap B)=f(A)\cap f(B)$.

An injection from a non-empty set has a left inverse.

A surjection has a right inverse. <em>[Uses choice.]</em>

$A\cap(B\cup C)=(A\cap B)\cup(A\cap C)$.

$(A\cap B)^c=A^c\cup B^c$.

<h3>Sequences and series.</h3>

A sequence that is unbounded above has a subsequence that tends to infinity. <em>[Requires building a sequence. Involves induction.]</em>
