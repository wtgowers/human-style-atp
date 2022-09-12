---
layout: post
title: "What library reasoning is acceptable in a motivated proof?"
<!-- subtitle: "A follow-up to the previous post" -->
date: 2022-09-12 17:00:00
background: '/img/maths_background.png'
author: "Timothy Gowers"
mathjax: true
---

Unfinished post.

## The problem

One of the central theoretical aims of the project is to come up with a finite set of move types that can be used to generate all proofs that a human would judge to be "motivated", in the sense that they do not involve drawing a rabbit out of a hat. (For basic definitions we use, such as that of a "move type", see <a href="{{site.baseurl}}/2022/09/07/basicalgorithm.html">this post</a>.) This problem splits naturally into two subproblems: say more precisely what counts as a "rabbit out of a hat", and devise the set of move types.

One clear example of a step that should count as a rabbit out of a hat is instantiation of a quantifier with a term that is not in any sense "present" in the current problem state. So we can insist that all instantiations must be with variables or more complex terms that have already been generated using moves from the small set of move types. (It is also important to place restrictions on what is allowed as a move type. For example, if we want to ban producing an arbitrary formula out of nowhere, we must make sure that our moves are not expressive enough to encode arbitrary formulae.)

A move type that is fundamental to doing mathematics is that of combining a hypothesis one has generated with a result one already knows in order to deduce a further piece of information. For instance, if one has established that a set $A$ is a compact subset of a topological space $X$ and that $f:X\to Y$ is a continuous function, one might want to deduce that $f(A)$ is a compact subset of $Y$. This raises the following question.

**Question.** *Under what circumstances should the use of a library result be classed as motivated?*
