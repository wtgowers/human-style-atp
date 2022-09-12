---
layout: post
title: "What library reasoning is acceptable in a motivated proof?"
subtitle: " "
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

It seems clear that there will have to be some restriction, since if every library reasoning step is permitted in a motivated proof, that would appear to make it possible to generate any proof, whether or not we would judge it to involve a miraculous idea.

To clarify the discussion a little bit, let us consider two different kinds of "miracles" that we would like to avoid.

1. Out of the blue we extract a result from the library and add it to our list of hypotheses, after which it becomes fairly straightforward to finish solving the problem. An example of this might be if we extracted the Baire category theorem, and then found that sure enough we could easily construct some dense open sets using the information we had been given, and also that the fact that those sets have a non-empty intersection was extremely useful.
2. We make a sequence of simple deductions that are going nowhere obvious and then suddenly there is a big payoff. An example of this might be a bit like the reverse of the previous example: we might "observe" that our hypotheses implied that certain sets were dense and open, thereby creating a perfect match for the hypotheses of the Baire category theorem, after which the idea of extracting the Baire category theorem from the library would be an obvious one.

I'm not sure how important the distinction between the above two forms of "lack of motivation" is. In one case we extract an apparently irrelevant result from the library, which, once we decide we are going to use it, provides us with plenty of motivation for the steps that follow -- we know we want to create some dense open sets, and so on. In the other case, we do a series of library modus ponens steps, and what makes it unmotivated is that there are many deductions we could have made from our hypotheses using library results, and no clear reason for choosing the ones we chose.

Now let's think what a motivated use of the Baire category theorem might look like. This is closely related to the question of how an experienced human mathematician might notice that the theorem can be applied. We might find, for instance, that we want to prove a statement of the form $\exists x\in X\ \forall n\in\mathbb N\ P(n,x)$, where $X$ is a metric space. We might observe that the weaker statement where the quantifiers are reversed, namely $\forall n\in\mathbb N\ \exists x\in X\ P(n,x)$, is quite easy to prove, in which case we would say to ourselves "It's fine if $x$ is allowed to depend on $n$, but I want it to hold *uniformly*." And then our experience would tell us that there are tools around that allow us, under suitable circumstances, to obtain uniform statements: roughly speaking we need each $P(n,x)$ to hold not just for *some* $x$ but for *almost all* $x$, where there are several possible interpretations of "almost all" that can be useful. Here we are discussing the category notion of "almost all" but another is the measure-theoretic notion, where the set of $x$ that do not satisfy $P(n,x)$ has measure zero. We might then look at the problem and see that there is no obvious measure about, but that it is definitely worth checking whether $\{x:P(n,x)\}$ is dense and open. We might even take note of encouraging hints of this, such as that the property $P(n,x)$ involves strict inequalities rather than non-strict ones.

There's quite a lot going on here, and much of it looks as though it might be quite hard to model. For instance, the explanation above relied on a somewhat vague and abstract notion of "suitable 'almost all' definition". However, while imprecise language often plays a role in the process by which human mathematicians discover proofs, it is not clear how essential it is for this kind of search. Maybe one could make it precise by defining a formal notion of "a system of small subsets of $X$", which would obey axioms such as "A countable union of small sets is small" and "$X$ is not small". Then we could have a very general library result that said that the statement $\exists x\in X\ \forall n\in\mathbb N\ P(n,x)$ is true if there is a system $\Sigma$ of small sets such that for every $n$ the set $\{x\in X:\neg P(n,x)\}$ is small. And finally there would be some library results to say that the nowhere dense sets in a metric space are a system of small sets, as are the sets of measure zero in $\mathbb R$.
