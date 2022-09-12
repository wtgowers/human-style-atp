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

## An example: using the Baire category theorem

To clarify the discussion a little bit, let us consider two different kinds of "miracles" that we would like to avoid.

1. Out of the blue we extract a result from the library and add it to our list of hypotheses, after which it becomes fairly straightforward to finish solving the problem. An example of this might be if we extracted the Baire category theorem, and then found that sure enough we could easily construct some dense open sets using the information we had been given, and also that the fact that those sets have a non-empty intersection was extremely useful.
2. We make a sequence of simple deductions that are going nowhere obvious and then suddenly there is a big payoff. An example of this might be a bit like the reverse of the previous example: we might "observe" that our hypotheses implied that certain sets were dense and open, thereby creating a perfect match for the hypotheses of the Baire category theorem, after which the idea of extracting the Baire category theorem from the library would be an obvious one.

I'm not sure how important the distinction between the above two forms of "lack of motivation" is. In one case we extract an apparently irrelevant result from the library, which, once we decide we are going to use it, provides us with plenty of motivation for the steps that follow -- we know we want to create some dense open sets, and so on. In the other case, we do a series of library modus ponens steps, and what makes it unmotivated is that there are many deductions we could have made from our hypotheses using library results, and no clear reason for choosing the ones we chose.

Now let's think what a motivated use of the Baire category theorem might look like. This is closely related to the question of how an experienced human mathematician might notice that the theorem can be applied. We might find, for instance, that we want to prove a statement of the form $\exists x\in X\ \forall n\in\mathbb N\ P(n,x)$, where $X$ is a metric space. We might observe that the weaker statement where the quantifiers are reversed, namely $\forall n\in\mathbb N\ \exists x\in X\ P(n,x)$, is quite easy to prove, in which case we would say to ourselves "It's fine if $x$ is allowed to depend on $n$, but I want it to hold *uniformly*." And then our experience would tell us that there are tools around that allow us, under suitable circumstances, to obtain uniform statements: roughly speaking we need each $P(n,x)$ to hold not just for *some* $x$ but for *almost all* $x$, where there are several possible interpretations of "almost all" that can be useful. Here we are discussing the category notion of "almost all" but another is the measure-theoretic notion, where the set of $x$ that do not satisfy $P(n,x)$ has measure zero. We might then look at the problem and see that there is no obvious measure about, but that it is definitely worth checking whether $\{x:P(n,x)\}$ is dense and open. We might even take note of encouraging hints of this, such as that the property $P(n,x)$ involves strict inequalities rather than non-strict ones.

There's quite a lot going on here, and much of it looks as though it might be quite hard to model. For instance, the explanation above relied on a somewhat vague and abstract notion of "suitable 'almost all' definition". However, while imprecise language often plays a role in the process by which human mathematicians discover proofs, it is not clear how essential it is for this kind of search. Maybe one could make it precise by defining a formal notion of "a system of small subsets of $X$", which would obey axioms such as "A countable union of small sets is small" and "$X$ is not small". Then we could have a very general library result that said that the statement $\exists x\in X\ \forall n\in\mathbb N\ P(n,x)$ is true if there is a system $\Sigma$ of small sets such that for every $n$ the set $\{x\in X:\neg P(n,x)\}$ is small. And finally there would be some library results to say that the nowhere dense sets in a metric space are a system of small sets, as are the sets of measure zero in $\mathbb R$. These results would not be what we normally think of as theorems. Rather, they would be formal statements of heuristic principles, and the purpose of having them in the library would be to model the know-how of an experienced human mathematician, providing a bridge between a problem state where a library result can be applied in a non-obvious way, and the library result itself. 

A slight worry here is that we don't want to cheat by simply adding motivating principles to the library every time we can't see how to find a motivation for extracting a library result. But I'm not too worried by that. If an undergraduate asked the question "How on earth did you think of using the Baire category theorem?" and received an explanation along the lines given above (about needing to have a suitable notion of "almost all" in order to obtain uniformity), then I think they would find it convincing. And if a human mathematician does *not* have a heuristic principle such as the above one in their personal library (that is, the bank of knowledge they carry around in their brain) then they will normally be quite bad at spotting that the Baire category theorem can be used. 

## Towards a criterion for when using a library result is motivated

I do not have a complete answer -- hence the word "towards" -- but let me try to find conditions that seem to be necessary and conditions that seem to be sufficient (but not necessarily a set of conditions that between them are necessary and sufficient). 

1. A sufficient condition for a piece of library reasoning to be motivated is if we identify a feature that we would like the problem state to have (such as a match for a term that is already present), and there is one and only one library deduction that will immediately give us that feature if we do it. (I'm assuming here that searching for a library result that will lead to the given feature can be done quite efficiently.)
2. A necessary condition for a piece of library reasoning to be motivated is that it leads to a noticeable improvement in the problem state. (The slight difference between this and the first condition is that the first is saying that we form a subtask out of the feature and make a specific effort to achieve that subtask. With this one we are just asking for something nice to happen if we do the deduction.)

I thought I was going to have more to say there, but actually I don't. I'm wondering whether the first condition might in fact be necessary and sufficient, at least when appropriately formulated. 

To test that thought, let me try to think about the Baire category theorem example once more. If we had the statement $\exists x\in X\ \forall n\in\mathbb N\ P(n,x)$ as a target, the proposal above was that we would use library reasoning to convert that into a statement that would say something along the lines of "There is a notion of smallness such that for each $n$ the set of $x$ such that $\neg P(n,x)$ is small." But what intermediate goal would be achieved by reformulating the target in this way?

As a human mathematician I might say something like this. "Typically, proving uniform statements is hard, and one needs suitable tools to do it. There aren't very many standard tools of this kind, so let's see if we can find one that works." But somehow that doesn't easily translate into the language of problem states and their features. That is, what would make the target
$$\exists\Sigma\ \forall n\in\mathbb N\ \text{is_small}_\Sigma\{x\in X:P(n,x)\}$$
preferable to the target
$$\exists x\in X\ \forall n\in\mathbb N\ P(n,x)?$$

A possible answer comes if we invent a new notation, writing $\AE_\Sigma\ x\ Q(x)$ to mean $\{x:\neg Q(x)\}\in\Sigma$. This would be read as "for almost all (in the sense of $\Sigma$) $x$, $Q(x)$". In this notation the first target would now read
$$\exists\Sigma\ \forall n\in\mathbb N\ \text{a.e.}_\Sigma\ x\ P(n,x).$$
This would be better than the first target because the quantifiers would have been reversed (at the cost of replacing "there exists" by the much stronger "for almost all (in the sense of $\Sigma$)".

But that still feels unsatisfactory, because the improvement is not a syntactic feature of the problem state, but rather a mathematical one -- we somehow know from experience that replacing a uniform statement by a non-uniform one has a good chance of being helpful. Maybe that idea can itself be encoded as a formal statement in the library, though I'm not sure I see how to do it.
