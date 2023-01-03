---
layout: post
title: "Automatic abstraction"
subtitle: " "
date: 2023-01-03 09:40:00
background: '/img/maths_background.png'
author: "Timothy Gowers"
mathjax: true
---

## Introduction 

It goes without saying that abstraction and generalization are fundamental mathematical activities. From the point of view of automatic theorem proving, it is tempting to regard them as relatively "advanced" topics, to be worried about only when simpler problem-solving techniques have been thoroughly understood and implemented. But it has been becoming clear that if we do not introduce at least some forms of abstraction and generalization into a program at an early stage, then that program will be quite limited in what it can do. The issue comes to a fore in connection with library search. Our main idea for how to carry out searches in the library for results that could be helpful is to find syntactic matches. However, while that works very well when it works, there are many situations where a useful result does _not_ syntactically match the problem state. And when that happens, it is often also the case that if aspects of the problem state are made more abstract, then we _do_ obtain a syntactic match. So the rough thinking behind this post is that relying on syntactic matching works surprisingly well for a number of problems, but combining it with abstraction will probably make it work a whole lot better.

I won't try to do everything in one post. Instead, this is meant to be the beginning of a discussion. I shall look at a few examples, and try to identify a few different kinds of generalization that could in principle be automated.

## Using Zorn's lemma

This is a typical example. Zorn's lemma is stated in Wikipedia as follows.

**Lemma** *Suppose a partially ordered set $P$ has the property that every chain in $P$ has an upper bound in $P$. Then the set $P$ contains at least one maximal element.*

A typical application of the lemma is that every vector space has a basis. The proof is to use Zorn's lemma to prove that there is a maximal independent set and then to prove that a maximal independent set must span the space. However, in order to find that proof we need to identify that we are trying to find a maximal object. Once we have uttered the word "maximal" we have a syntactic match with at least one word in the statement of Zorn's lemma, and though no partially ordered set has been mentioned explicitly, the use of "maximal" strongly suggests that there is one somewhere. But the point is that a process of abstraction is needed. Furthermore, in order to obtain the syntactic match it is important that the lemma is stated using high-level language (as opposed, say, to the conclusion being the statement
$$\exists x\in P\ \forall y\in P\ \neg(x < y),$$
which would be hard to match with anything).  

Suppose that we are thinking about this problem. We might start trying to build a basis. If we do so, then we will start adding vectors, taking care at each stage not to create a linear dependence. If at any stage we span the space, then we are done, so it is natural to use the hypothesis that the set does not span the space. That provides us with a vector that is not in the span, which implies quite easily that we can add it to our independent set. 

It is at this point that we want to abstract. We have a statement about independent sets in a vector space, which says that if such a set $I$ does not span, then we can find a non-zero element $x$ such that $I\cup\\\{x\\\}$ is independent. We now want to make the more general observation that $I$ is not maximal under set-theoretic containment. To enable a syntactic match, there are two things we can do here. One is to restate Zorn's lemma in a way that involves set-theoretic containment rather than an abstract partial order. The other is to forget some of the details about our problem: we don't care that the sets we are interested in are the independent sets -- they are just some family of sets -- and we don't care that $I\cup\\\{x\\\}$ is obtained from $I$ by the addition of a singleton -- we just need it to strictly contain $I$. 

This second process illustrates one kind of abstraction, namely forgetting hypotheses. 

If we don't rewrite Zorn's lemma, then there is a second kind of abstraction that we will need to use, which one can think of as replacing a mathematical object by a more general class of objects -- in this case, replacing set-theoretic containment by an arbitrary partial ordering. This is a sort of forgetting, but it is not forgetting hypotheses that have been written down. Rather, it is a more conscious kind of forgetting. Another example would be forgetting everything about $\mathbb Z$ except that it forms an Abelian group under addition. 

What exactly is the difference? The second form of abstraction can be described as follows. One has an object (such as $\mathbb Z$), one notes that it has certain properties (such as the Abelian group properties), and then one forgets everything about the original object other than those properties. With any luck there is a name for the resulting abstract concept, but if not, then one can give it a temporary name. 

## Using the Baire category theorem

The Baire category theorem is another result with several applications that are somewhat non-obvious, in the sense that one is often not handed on a plate a countable collection of sets that are open and dense, or alternatively a decomposition of a complete metric space as a union of countably many closed sets. So if a little bit of work is needed to massage the problem state into a form where the Baire category theorem can be applied, what will induce a program to guess that this can be done? I don't yet have a fully satisfactory answer, so instead I shall discuss several examples. 

### The open mapping theorem

A classic application of the Baire category theorem is the open mapping theorem, which is the following statement.

**Theorem** _Let $X$ and $Y$ be Banach spaces and let $T:X\to Y$ be a surjective continuous linear operator. Then $T(U)$ is open for every open set $U\subset X$._

What might make us think of using the Baire category theorem here? I had forgotten the proof myself, so I had a go at it. If we look at the contrapositive, we find that we have an open set $U$ with an image $T(U)$ that is not open. Picking $x\in U$ we find that $T(U)$ does not contain any ball around $Tx$, but $U$ contains a ball around $x$. Thus, there is a ball $B_\epsilon(x)$ around $x$ such that $T(B_\epsilon(x))$ does not contain any ball $B_\delta(Tx)$. We can therefore find $(y_n)$ with $y_n\to Tx$ such that no $y_n$ belongs to $T(B_\epsilon(x))$. By linearity, we therefore have $(y_n)$ with $y_n\to 0$ such that no $y_n$ belongs to $T(B_\epsilon(0))$. 

It would be tempting to try to use the vectors $y_n$ to create a vector $y$ that is not in the image of $T$, but that seems to be hard. And here is a potential trigger for the use of the Baire category theorem. Perhaps instead of _constructing_ a vector $y$ that does not belong to the image of $T$, we can instead attempt to prove that _almost every_ vector $y\in Y$ has that property, according to some appropriate definition of "almost every". Since there are no measures about, our best bet is probably to use the Baire category theorem to prove that $TX$ is meagre in $Y$. 

This is still quite a speculative step, but if we can write $TX$ as a countable union in a natural way, then it will start to become more promising. We have already looked at images of balls around 0, so it is fairly natural to observe that $TX=\bigcup_{n=1}^\infty T(B_n)$ (where I'm writing $B_n$ for the open ball of radius $n$ about 0). We'll therefore be done if we can prove for each $n$ that $T(B_n)$ is nowhere dense. That is not completely straightforward, but it can be done. I don't want to dwell on it too much here, since my main focus is the trigger for using Baire category. 

### Perfect sets are uncountable

A set of reals is _perfect_ if it is closed and has no isolated points. Such sets can be shown to be uncountable. Here the trigger for Baire category is very simple: if a perfect set $X$ is countable, then it is a countable union of singletons, so we know we will be done if (i) $X$ is a complete metric space and (ii) every singleton in $X$ is nowhere dense. That is almost a syntactic match but maybe not quite -- there is a small step to take us from saying that $X$ is countable to saying that it is a countable union of singletons, and that step does sometimes hold me up when I try to remember the proof (even when I remember that it is a simple application of the Baire category theorem). 

It's easy to check that $X$ is complete, since it's a closed subset of a complete metric space. Also, if $x$ is a singleton and $U$ is an open subset of $X$, then $U\setminus\\\{x\\\}$ is a non-empty (because $x$ is  not isolated) open subset of $X$ that does not intersect $\\\{x\\\}$.

### A continuous function that is nowhere monotonic

Quite often the trigger for Baire category is not so much a trigger as a proof strategy, namely to prove that a generic object does what one wants, as a way of avoiding actually constructing one. 

So here one might decide to try to prove that the set of functions that are monotonic in an interval is meagre in the set of all continuous functions (where the metric is given by the uniform norm, so actually I'll be talking about bounded continuous functions). Having made that decision, it is natural to observe that if a function is monotonic on an interval, then it must be monotonic on an interval with rational end points, so it is sufficient to prove that the set of bounded continuous functions that are monotonic on $(a,b)$ is nowhere dense. And that's easy to do: given a continuous function $f$, we can approximate it by a function $g$ that has both a decreasing and an increasing part in $(a,b)$, and any function $h$ that is sufficiently close to $g$ will also fail to be monotonic. 

### The rationals do not form a $G_\delta$ set

A $G_\delta$ set is a countable intersection of open sets. Can the rationals be expressed in this way? We can certainly write \emph{one} rational as such an intersection: for example, $\\\{0\\\}=\bigcup_{n=1}^\infty(-1/n,1/n)$. But what about all rationals at once? 

This is a very easy application of Baire category, since if $\mathbb Q=\bigcap_{n=1}^\infty U_n$ with each $U_n$ open, then each $U_n$ is open and dense, which implies that $\mathbb Q$ has meagre complement. But we also know that $\mathbb Q$ is meagre (since it is a countable union of singletons), which contradicts the Baire category theorem. 

But what is the trigger here? These questions are all quite hard to answer, because the results are usually presented as applications of the Baire category theorem, so one does not have the opportunity to think for oneself of using it. However, I would suggest the following. It is very natural to think about what would happen if $\mathbb Q=\bigcap_{n=1}^\infty U_n$. Having done that, it is natural to think about the properties that the $U_n$ must have, and to observe that each one is open and contains $\mathbb Q$. Furthermore, one of the main properties of $\mathbb Q$ in an analysis context is that it is dense -- this could be regarded as an abstraction step actually, the idea that certain properties of $\mathbb Q$ are all that matter for the problem. In any case, it doesn't seem a huge step to notice that $U_n$ must be open and dense, and that is a big trigger for Baire category, only reinforced by the fact that there are countably many of the $U_n$. So I think my answer in this case would be a little bit of forward reasoning followed by a syntactic match. 

### Can a function be continuous at the rationals and discontinuous at the irrationals?

Let me quote from [some nice notes I'm looking at](https://www.ucl.ac.uk/~ucahad0/3103_handout_7.pdf): "After spending an hour or two trying to construct such a function, one begins to suspect that no such function can exist. But how to prove it? Once again, the Baire category theorem comes to the rescue."

But how? Well, we could try to think about what sorts of sets can be sets of continuity of a function $f$. So we write down something like this.
$$X=\\\{x\in\mathbb R:\forall\epsilon>0\ \exists\delta>0\ \forall y\in\mathbb R\ \ |x-y|<\delta\implies|f(x)-f(y)|<\epsilon\\\}.$$
If we want to think about what type of set that is, using standard notions of complexity, then we can observe two things. The first, which is very standard, is that quantifiers inside sets become unions or intersections outside. But also we prefer countable unions, and we notice that in this case it makes no difference if we assume $\epsilon$ and $\delta$ to be reciprocals of positive integers. So we can write the set as follows.
$$X=\bigcap_{n=1}^\infty\bigcup_{m=1}^\infty\\\{x\in\mathbb R:\forall y\in\mathbb R\ \ |x-y|<1/m\implies|f(x)-f(y)|<1/n\\\}.$$
At this point we have a problem, because for a given $m,n$ there is not much we can say topologically about the set
$$A_{nm}=\\\{x\in\mathbb R:\forall y\in\mathbb R\ \ |x-y|<1/m\implies|f(x)-f(y)|<1/n\\\},$$
especially given that $f$ is not continuous. 

However, one thing we can say is that if $x\in A_{nm}$ and $|x'-x|<1/2m$, then $x'\in A_{n/2,2m}$. This suggests a better possible definition of the set of points of continuity, one that leads to open sets. Note that $f$ is continuous at $x$ if and only if for every $\epsilon>0$ there exists $\delta>0$ such that the difference between $\sup f$ and $\inf f$ on the interval $(x-\delta,x+\delta)$ is at most $\epsilon$. Let us write this as $\text{osc}_{(x-\delta,x+\delta)}(f)<\epsilon$. The advantage of this definition is that if we slightly perturb $x$, we get the same $\epsilon$ (for a smaller $\delta$). 

So let
$$B_{nm}=\\\{x:\text{osc}\_{(x-1/m,x+1/m)}(f) < 1/n\\\}.$$
Then from what we noted above, although $B_{nm}$ isn't open, $\bigcup_{m=1}^\infty B_{nm}$ is open, since if we move $x$ by $1/2m$, we still belong to $B_{n,2m}$. This proves that $X$ is a $G_\delta$ set and therefore that it cannot equal $\mathbb Q$. 

This turned out to be irrelevant to the question of triggers for the Baire category theorem, since it used a _consequence_ of the Baire category theorem.

### The uniform boundedness theorem

Here's another theorem I used to know and will try to reconstruct. It is the following.

**Theorem** *Let $X$ and $Y$ be Banach spaces and for each $\gamma$ in a set $\Gamma$ let $T_\gamma$ be a continuous linear map from $X$ to $Y$. Suppose that for each $x$ there is some $C_x$ such that $\|T_\gamma x\|\leq C_x\|x\|$ for every $\gamma\in\Gamma$. Then there is some $C$ such that $\|T_\gamma x\|\leq C\|x\|$ for every $x\in X$ and every $\gamma\in\Gamma$. That is, if the $T_\gamma$ are pointwise bounded, then they are uniformly bounded.*

This is often the flavour of a consequence of the Baire category theorem -- that we get an unexpected uniformity. And how do we get it? By arguing that some countable collection of open dense sets $U_n$ has a non-empty intersection, where typically $U_n$ will be of the form $\{x:P_n(x)\}$. In this case, since we are trying to prove a universally quantified statement, the only way in which finding some $x\in X$ is going to be useful is if we are aiming for a contradiction. 

So let's turn things round. We assume that for every $n$ there exist $x$ and $\gamma$ such that $\|T_\gamma x\|>n\|x\|$, and our aim is to interchange the order of quantification, obtaining $x$ such that for every $n$ there exists $\gamma$ with $\|T_\gamma x\|>n\|x\|$, which will contradict pointwise boundedness. To do that, we will want to prove not just that there _exists_ $x$ such that for some $\gamma$ we have $\|T_\gamma x\|>n\|x\|$ but that the set of $x$ such that that can be done is both open and dense.

Now for each $n$ and $\gamma$ the set $\\\{x:\|T_\gamma x\|>n\|x\|\\\}$ is open (this is easy to prove, since the map $x\mapsto\|T_\gamma x\|-n\|x\|$ is continuous). Therefore, the union over all $\gamma$ is open, and this union is equal to $U_n=\\\{x:\exists\gamma\ \ \|T_\gamma x\|>n\|x\|\\\}$.

Can we prove that $U_n$ is dense? Yes, fairly easily. Let $x\in X$. I would like to find a point $x'$ close to $x$ and some $\gamma$ such that $\|T_\gamma x'\|>n\|x'\|$. To do that, note first that either I can take $x'$ to equal $x$ or else $\|T_\gamma x\|\leq n\|x\|$ for every $\gamma$. In the second case, for every $C$ I can find $\gamma$ and $z$ such that $\|z\|<\delta\|x\|$ and $\|T_\gamma z\|>3n\|x\|$. Then assuming $\delta\leq 1$, we have that $\|x+z\|<2\|x\|$ and that $\|T_\gamma(x+z)\|>3n\|x\|-n\|x\|=2n\|x\|>n\|x+z\|$. So we have found $x+z$ as close as we like to $x$, and some $\gamma$ that proves that $x+z\in U_n$. 

### What just happened?

In this case, the trigger was the "unexpected uniformity". Since that is a fairly good example of abstraction, it is worth dwelling on it a bit further. 

First of all, recognising that we have a pointwise statement and want a uniform one is easy: it's just a question of spotting that we have what we want except that the order of quantification is $\forall a\ \exists b$ instead of $\exists b\ \forall a$. But how do we convert that observation into a successful library search for a program using abstraction and syntactic matching? 

I think that part of the answer has to be to have a version of the Baire category theorem that is closer to what we notice than to the official statement of the theorem. For example, it could read as follows (translated into a suitable formal language).

**Theorem** _Let $P(n,x)$ be a statement involving two variables $n\in\mathbb N$ and $x$ an element of a complete metric space $X$. Suppose that the following conditions hold._
1. _$\forall n\in\mathbb N\ \\\{x\in X:P(n,x)\\\}$ is open._
2. _$\forall n\in\mathbb N\ \\\{x\in X:P(n,x)\\\}$ is dense._

_Then $\exists x\in X\ \forall n\in\mathbb N\ P(n,x)$._

This is obviously equivalent to the Baire category theorem, but because of the way it is stated, it is easier to pick up a syntactic match with the target.

If we use the closed-sets version, then we can obtain a match without first switching to the contrapositive. The closed-sets version can be restated in a similar way as follows.

**Theorem** *Let $P(n,x)$ be a statement involving two variables $n\in\mathbb N$ and $x$, an element of a complete metric space $X$. Suppose that the following conditions hold.*
1. *$\forall x\in X\ \exists n\in\mathbb N\ P(n,x)$.*
2. *$\forall n\in\mathbb N\ \\\{x\in X:P(n,x)\\\}$ is closed.*

*Then there exist $n\in\mathbb N$ and an open set $U\subset X$ such that $\forall x\in U\ P(n,x)$.*

Now we see that we have the first hypothesis, and it becomes worth checking whether we have the second, and whether the conclusion, which appears to be weaker than we want (it gives us uniformity on an open set rather than on all of $X$), is in fact sufficient (which it is). 

### A problem about nilpotent operators

Let $X$ be a Banach space and let $T:X\to X$ be a continuous linear operator. Let us say that $T$ is _pointwise nilpotent_ if for every $x$ there exists $n$ such that $T^nx=0$, and _nilpotent_ if there exists $n$ such that $T^n=0$. I have just read that every pointwise nilpotent operator is nilpotent.

Let me try to prove that. Again the trigger is fairly clear here -- we are trying to convert a pointwise statement into a uniform one. So it seems that the same strategy as before should work, namely to assume that $T$ is not nilpotent and deduce that it is not pointwise nilpotent. However, this time I'll go with the closed-sets version. As discussed above, the trigger is simple: we have a hypothesis of the form $\forall x\ \exists n\ P(n,x)$, and it looks as though the relevant sets will be closed since we have an equality sign and a continuous function around the place. 

Let's quickly finish off the proof. From Baire category we get some $n$ such that $\\\{x:T^nx=0\\\}$ has non-empty interior. If it contains a ball $B_\delta(y)$, then it also contains $B_\delta(-y)$, by linearity, and then it contains $B_\delta(0)$, by convexity. So $T^nx=0$ for every $x$ of norm less than $\delta$, which of course implies that $T^n=0$. 

### Conclusion on Baire category triggers

It seems that there are several ways in which the Baire category theorem can be triggered. Let me list a few of them (but I don't claim that this is a complete list). 

1. We have a hypothesis of the form $\forall x\in X\ \exists n\in\mathbb N\ \ P(n,x)$, where $X$ is a complete metric space, and we want to prove that $\exists n\in\mathbb N\ \forall x\in X\ P(n,x)$. (This can be generalized by replacing $\mathbb N$ by another countable set. Also, it may be that we can make do with just the hypothesis or the conclusion being given explicitly.) 
2. We are trying to prove a statement of the form $\exists n\in\mathbb N\ \forall x\in X\ \ P(n,x)$ and it seems potentially difficult to construct such an $x$.
3. We are trying to construct an object with given properties and we suspect that a generic object might have the properties we want. (This is of course a bit vague, so I am not yet satisfied with it as a trigger that can be automated.) 
4. We want to prove that a given set cannot be an intersection of countably many open sets.

Note that sometimes the trigger is quite specific and not much abstraction is needed: for example, with the statement that $\mathbb Q$ is not a $G_\delta$ set, we are given a countable intersection of open sets, so there is a fairly direct match with the usual formulation of the Baire category theorem, whereas with the statement about nilpotent operators we need to abstract away to the point where all we see is that we are in the situation 1 above (so we forget that we have Banach spaces and a linear operator etc.). 

## Some simpler examples where abstraction takes place

Sometimes use of abstraction is considerably simpler than in the examples discussed so far. Here are a couple of examples.

### Using the nested-intervals property

The use of the nested-intervals property is one where one is often not presented with nested intervals on a plate, but rather one constructs them in order to prove a statement. Typically this works in a Baire-category-ish way: one wishes to prove a statement of the form $\exists x\ \forall n\ \ P(n,x)$, and the strategy is to obtain the properties one by one, but in order not to commit oneself too much to a particular $x$ right at the beginning, one instead finds an interval $I_1=[a_1,b_1]$ such that $P(1,x)$ holds for every $x\in I_1$, and then an interval $I_2=[a_2,b_2]\subset I_1$ such that $P(2,x)$ holds for every $x\in I_2$, and so on. 

A suitable formulation of the nested-intervals property for this purpose might be this.

**Theorem** *For each $n$ let $P_n$ be a property of real numbers. Suppose that there exists a sequence $I_1\supset I_2\supset\dots$ of non-empty closed intervals such that $P_n(x)$ holds for every $n\in\mathbb N$ and every $x\in I_n$. Then there exists $x$ such that $\forall n\in\mathbb N\ P_n(x)$.* 

I think the trigger here is simply noting that the target is of the form $\exists x\in\mathbb R\ \forall n\in\mathbb N\ P_n(x)$. 

### Proving that certain sets are closed

Suppose that $f$ and $g$ are continuous functions from $\mathbb R$ to $\mathbb R$ and that you are asked to prove that $\\\{x\in\mathbb R:f(x)\geq g(x)\\\}$ is closed. With a bit of experience you will probably reason as follows: since $f$ and $g$ are continuous, so is $h=f-g$, and the set we wish to prove is closed is the set $h^{-1}([0,\infty))$. Since $h$ is continuous and $[0,\infty)$ is closed, we are done. 

What triggers the use of the library results that a difference of two continuous functions is continuous and that the inverse image of a closed set under a continuous function is closed? 

Again it seems that it would help to have a reformulation of a familiar fact in the library. Instead of the usual result that says that the inverse image of a closed set by a continuous function is closed, we could have this.

**Lemma** *Let $X$ and $Y$ be topological spaces and let $f:X\to Y$ be continuous. Let $P$ be a property of elements of $Y$ and suppose that the set $\\\{y\in Y: P(y)\\\}$ is closed. Then $\\\{x\in X:P(f(x))\\\}$ is a closed subset of $X$.*

If we had that, then we could spot the potential utility of the lemma as follows. First, we abstract the lemma, noting that its conclusion is of the form "$\\\{x\in X:Q(x)\\\}$ is closed" for some property $Q$ that satisfies suitable conditions. We then note that we want to prove a statement of that form. So now we have a subtask, which is to rewrite the statement $f(x)\geq g(x)$ in the form $P(h(x))$. For that we need to manipulate the parse tree of the statement $f(x)\geq g(x)$ so that we don't have two occurrences of $x$ in expressions being joined by a relation: we need a single expression that involves $x$. There are in fact two quite natural ways of doing this. One is to note that this is saying that $((f(x),g(x))$ belongs to the set $\\\{(u,v):u\geq v\\\}$, and the other is what I did above and replace the inequality by $f(x)-g(x)\geq 0$. Either works. 

But the important point here is that the use of the lemma was triggered by two abstractions, one of the conclusion of the lemma and one of the conclusion we actually wanted. 

More generally, why is this important? Note that the more we abstract in this way, the less likely it is that the result we find in the library will be useful, since we may have abstracted away features that are important. Suppose, for example, that I have a subset $A$ of a metric space $X$, I define $B$ to be the set of limit points of sequences in $A$, and I ask for a proof that $B$ is closed. Then 
$$B=\big\\\{x\in X:\exists (a_n)\ (\forall n\ a_n\in A)\ \wedge\ a_n\to x\big\\\}.$$
This is a set of the form $\\\{x\in X:Q(x)\\\}$, but it isn't of the form $P(f(x))$. 

Actually, this example makes me dissatisfied with the trigger I suggested above. It seems that there is a bit more going on, since if we don't have any functions $f:X\to Y$ around, it seems unlikely that we are going to be able to build a property of the form $P(h(x))$. And I'm not sure I'd be happy with the lemma above being triggered if we were faced with the example just given. 

Just to confuse things a bit more, here's another problem: prove that $\\\{x\in\mathbb R:x^3\geq e^x\\\}$ is a closed set. 

As a human, I think I am triggered to use the lemma by the fact that there is a property involved that applies not to $x$ but to things made out of $x$. But for that it seems that I depend on my mathematical experience to some extent to know that a property of the form $P(f_1(x),\dots,f_k(x))$ can often be transformed into one of the form $Q(f(x))$. Or I could simply regard $(f_1(x),\dots,f_k(x))$ as a function of $x$, but I'm slightly worried about that because I don't want to be forced to go for the product-set approach rather than the subtraction approach in the problem above. 

But maybe the _trigger_ should be simply that we are trying to prove that a set of the form $\\\{x\in X:Q(f(x))\\\}$ is closed, where by $f(x)$ I mean any expression of the form "element of a topological space" with the exception of $x$ itself. But that requires us to recognise a sentence such as
$$\mathtt{is\ greater\ than}(f(x),g(x))$$
as being of the form $Q(h(x))$, where $h(x)$ belongs to the topological space $\mathbb R^2$. But I think that that ought to be possible.

Then, having sorted out the trigger, one would consider having a separate simplification stage where we did things like replacing $\mathtt{is\ greater\ than}(f(x),g(x))$ by 
$$\mathtt{is\ non-negative}(f(x)-g(x)).$$

### Two kinds of abstraction

Before I move on, I should mention that part of the abstraction there was passing from $\mathbb R$ to a statement about topological spaces. So let me try to be clear about the difference here. One kind of abstraction occurs when we take a node of a parse tree and forget everything about it apart from its type (and possibly the fact that it is identical to another node somewhere). For instance, we might have some statement involving $x$, where $x$ is an element of $\mathbb R$, and we might abstract by deciding that that is all we care about -- that that node is of the form $Q(x)$ for some property $Q$. 

The other kind of abstraction occurs when we replace the type of a node by a more general type. For instance, we might have two subspaces of a vector space but care only that they are two subsets of a set. Or we might not care that $\mathbb R$ is $\mathbb R$ but only that it is a metric space. To do that kind of abstraction automatically, we have to check that we have removed from the parse tree (by abstracting) everything that relies on the structure we are forgetting. For example, suppose we want to prove that if $a_n\to a$ then $a_n^3\to a^3$. If we prove it using the fact that the function $x\mapsto x^3$ is continuous and continuous functions preserve convergence, then we will \emph{first} have to abstract away the function $x\mapsto x^3$ so that it becomes just an arbitrary continuous function $f$, and only then will we have a problem state that makes sense for a general metric space.

How would that work? Unless we want to annotate our parse trees with lots of potentially irrelevant observations (which isn't necessarily a ridiculous idea) I think we would need to replace the function $x\mapsto x^3$ by an arbitrary function, then do a syntactic match with the result that continuous functions preserve convergence, then spot that we have all the hypotheses we need apart from the fact that $x\mapsto x^3$ is continuous, and end up with a new target to show that that's the case, which would be done with some more library reasoning.

Actually, that's a nice further example.

### The function $x\mapsto x^3$ is continuous

We could of course prove this directly, but what if it was just a quick thing we wanted to check as part of a bigger problem? Probably we'd just appeal to a library result that said that polynomials are continuous. But for that we need to recognise that we have a polynomial function of $x$, which feels like another kind of abstraction, distinct from the two above. Note that forwards reasoning feels appropriate here: we don't think to ourselves, "Well, we'd be done if the function $x\mapsto x^3$ is a polynomial, so let's check whether that's the case." Rather, we _notice_ that the function is a polynomial and deduce quickly from that that it is continuous. (I feel I also have a more general reaction, which says something like "polynomials are so nice that they have pretty well every smoothness property I could possibly want," but maybe we don't have to worry about that just yet.) 

But what is going on when we look at a polynomial expression and recognise it as such? More importantly, how do we want a program to do this? 

I wonder whether what's going on here is actually a different kind of abstraction. Suppose I am asked to prove that a more complicated function such as $x\mapsto e^{\sin x+x^3}-15x(x+\cos x)$ is continuous. I see after a very quick scan of the formula that it involves nothing but familiar unary and binary operations such as addition, subtraction, multiplication and trigonometric and exponential functions. So I know immediately that it will be continuous, and that I would be able to prove it using my repertoire of known continuous functions, together with rules such as that a products, sums, and compositions of continuous functions are continuous. And I could do the same for "differentiable". Also, in both cases I'd know what danger signs to look out for: in the case of continuity, division by zero, definition by cases, etc., and the same in the case of differentiability, but with the addition of things like worrying about $|x|$, the binary operations $\max$ and $\min$, and so on. 

Here we seem to have an example where instead of a formal library result, we have a more informal principle in our heads, which says something like, "If the formula for $f$ has only `nice' nodes in its parse tree, then $f$ is continuous." This could be regarded as abstraction of yet another kind. Then if we want to prove that a given function is continuous, we don't look for a specific result straight away. Rather, we do a quick scan of the parse tree and check that all the nodes are ones we know to preserve continuity. If it happens that all the nodes are addition, subtraction or multiplication and all the leaves are either scalars or $x$, then the program has the option of saying something more specific, namely that the function is a polynomial. (It is slightly more complicated to test for the function being a polynomial if it is explicitly written using positive integer powers, but still not hard -- there can be integer leaves as well, but they have to be part of a subterm of the form $\mathtt{power}(T(x),n)$.)

## Potential abstraction moves

Suppose we had a point-and-click system. Then one could imagine the following moves being possible. The main purpose in each case would be to make it easier for the program to find syntactic matches with library results.

### Forgetting internal structure of parse tree nodes}

For this one could click on a node of the parse tree (or a part of a mathematical expression that determines the node) and from a resulting menu choose "forget internal structure". The effect of this would be to replace the expression by a general expression of the same type, which would depend on the same set of free variables. For instance, if one started with the expression 
$$\mathtt{is\_closed}\Big(\big\\\{x\in\mathbb R:x^3\geq e^x\big\\\}\Big),$$
and one clicked on the '$\geq$' symbol, that would indicate that the subexpression to be abstracted away was the statement $x^3\geq e^x$, which depends on the free variable $x$ (free relative to the statement -- obviously in the entire expression it is bound). The forgetting move would replace it by the generic $P(x)$, to stand for some arbitrary statement that concerns $x$. 

If this were a genuine user interface, one might want to create a copy of the original expression, so that the original was left untouched. Or perhaps the abstracted '$P(x)$' could hover just above the original expression $x^3\geq e^x$.

### Passing to a more general structure

When proving facts about sets of real numbers, sometimes we care about arithmetic properties of $\mathbb R$, sometimes just about order properties, sometimes about metric-space properties, sometimes about topological properties, sometimes just about set-theoretic properties, and so on. All the examples I can think of where one might want to abstract away from $\mathbb R$ to whatever more general structure we care about are ones where we have results in the library about the general structures that are not explicitly stated for $\R$. And I'm not sure what we will want to do here. For example, if $x,y$ and $z$ are real numbers and I know that $x\leq y$ and $y\leq z$, how do I deduce that $x\leq z$? There seem to be at least three options.
1. Allow polymorphism as we tend to do in human mathematics, so '$\leq$' can stand for many different partial orders and we won't use the notation unless transitivity is satisfied. So we could match the hypotheses directly to the hypotheses of a library result.
2. Have different relations for each set, so in this case use `$\leq_{\mathbb R}$', and have separate library results for each one.
3. Have a single library result -- the transitivity axiom for partial orders -- and use an abstraction move to pass from $\mathbb R$ to a partially ordered set.
In the third case, if the initial problem state is 
$$x\in\mathbb R\ \wedge\ y\in\mathbb R\ \wedge\ z\in\mathbb R\ \wedge\ x\leq y\ \wedge y\leq z\implies x\leq z,$$
then one might click on one of the $\mathbb R$s and choose from a menu of potential generalizations, which would need to have enough structure to allow '$\leq$' to make sense -- so a few candidates would be ordered fields, totally ordered sets, and partially ordered sets. We would then choose partially ordered sets, and perhaps be given a "Replace all?" option so that we didn't have to change the other two $\mathbb R$s by hand. 

I'm not sure how useful this kind of abstraction move will be for the purposes of library search, but it seems worth mentioning.

### Forgetting internal structure but remembering properties

Suppose that we had a subexpression $x^3+x+1$ and thought that what mattered about it was that it was a polynomial of odd degree. We might want to replace the subexpression by $p(x)$, together with the hypotheses "$p$ is a polynomial" and "$\text{deg}(p)$ is odd". How might that be done with a point-and-click system? I think we would have to hard code in a simple polynomial-recognising algorithm, which, when you clicked on the $\mathtt{plus}$ of $\mathtt{plus}(x^3,x,1)$, would offer you the option "forget internal structure" but if you chose that, would offer "Retain properties?" as a follow-up option. If you accepted that, it would give you an automatically generated menu that would have properties such as $\mathtt{is polynomial}$, $\mathtt{is\ continuous}$, $\mathtt{is\ differentiable}$, $\mathtt{is\ increasing}$, and so on. Maybe it would even offer a $\mathtt{derive\ property?}$ option, which would allow you to formulate a subproblem to prove that your object had some given property, which would then be remembered. But I'm not sure how that would work in practice. I'm even less sure how with a point-and-click system one would identify the degree of the polynomial, unless the program offered it automatically as a menu option. 


