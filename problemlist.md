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

$\overline{\overline{A}}=\overline{A}$ for every set $A$. <em>[Should be routine. Good test problem.]</em>

If $f(\overline{A})\subset\overline{f(A)}$ for every $A$ then $f$ is continuous. <em>[Routine but a bit tricky. Good test problem.]</em>

If $f$ is continuous then $f(\overline{A})\subset\overline{f(A)}$ for every $A$. <em>[Routine but a bit tricky. Good test problem.]</em>

If $f$ is continuous then for every neighbourhood $N$ of $f(x)$ there is a neighbourhood $M$ of $x$ such that $f(M)\subset N$. <em>[Should be routine. Good test problem.]</em>

If for every $x$ and for every neighbourhood $N$ of $f(x)$ there is a neighbourhood $M$ of $x$ such that $f(M)\subset N$, then $f$ is continuous. <em>[Should be routine. Good test problem.]</em>

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

<h3>Sets and functions.</h3>

$f^{-1}(A\cup B)\subset f^{-1}(A)\cup f^{-1}(B).$ <em>[Very routine. Should be easily solvable by ROBOT.]</em>

$f(f^{-1}(B))\subset B.$ <em>[Very routine. Should be easily solvable by ROBOT.]</em>

$A\subset f^{-1}(f(A)).$ <em>[Very routine. Should be easily solvable by ROBOT.]</em>

If $f$ is an injection, then $f(A\cap B)=f(A)\cap f(B)$. <em>[Easy, but good test problem to see whether a system can handle equality in a satisfactory way.]</em>

An injection from a non-empty set has a left inverse. <em>[Involves the tricky issue that the left inverse needs to be defined everywhere, even if lots of values don't matter. So a good test problem and possibly hard to solve without cheating.]</em>

A surjection has a right inverse. <em>[Uses choice, so opens up quite a big can of worms. But maybe useful for that reason, particularly if our focus is on "classical" proofs.]</em>

$A\cap(B\cup C)=(A\cap B)\cup(A\cap C)$. <em>[Requires splitting into cases, so good test problem for technical reasons.]</em>

$(A\cap B)^c=A^c\cup B^c$. <em>[Requires splitting into cases, so good test problem for technical reasons.]</em>

<h3>Sequences and series.</h3>

A sequence that is unbounded above has a subsequence that tends to infinity. <em>[Requires building a sequence. Involves induction. This would be quite an ambitious target, though the sort of problem we'll need a system to be able to solve easily if it's going to be able to do even moderately interesting constructions in analysis.]</em>
