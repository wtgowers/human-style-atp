---
layout: page
title: Examples of motivated proofs
description:
background: '/img/maths_background.png'
mathjax: true
---

<p>This page will mostly consist of links to files that contain examples that people have come up with of proofs (or more precisely proof write-ups) that we would like to count as "motivated". Informally, this means that it is clear where every proof step has come from. In particular, if an existential statement is to be proved, or a universally quantified statement is to be instantiated, it is not enough simply to substitute in an expression that works: the expression has to emerge as a "solution", often as a result of the problem being "reduced" to something significantly simpler.</p>

<p>We illustrate this with a simple but non-trivial example: that of showing that there is no surjection from a set \(X\) to its power set \(\mathbb P X\). In order to prove this, it is sufficient to take an arbitrary function \(f:X\to\mathbb P X\) and exhibit a subset of \(X\) that does not belong to the image of \(f\). The usual "unmotivated" approach to this is simply to write, "Consider the subset \(Y=\{x\in X: x\notin f(x)\}\) of \(X\)," and then to proceed with the simple proof that shows that \(Y\) has no preimage under \(f\). We regard this as unmotivated because the definition of the set \(Y\) comes out of nowhere and "just happens to work".</p>

<p>A motivated presentation of the same proof can be given as follows. Instead of saying what \(Y\) is, we treat it as an unknown that we have to "solve for". So \(Y\) is a subset of \(X\) and we need the statement \(f(y)=Y\) to lead to a contradiction. Using the definition of set equality, we find that we want to derive a contradiction from the statement \(\forall x\ x\in f(y)\iff x\in Y\). For that it is sufficient to choose a value of \(x\) that will lead to a contradiction. But there is only one element of \(X\) that has been mentioned, namely \(y\), so let us try to derive a contradiction from the statement \(y\in f(y)\iff y\in Y\). Since we know nothing about \(y\), we shall need \(Y\) to have the property that \(y\notin Y\) whenever \(y\in f(y)\) and \(y\in Y\) whenever \(y\notin f(y)\). In other words, we shall have to take \(Y\) to be \(\{y\in X:y\notin f(y)\}\). Taking that set, we have the desired contradiction.</p>

<p>In the second presentation, we did instantiate a quantifier when we chose to set \(x\) to equal \(y\). But that choice did not come out of nowhere, as \(y\) was very much present in the problem -- indeed, as commented, it was the only element of \(X\) that had been mentioned. As for the definition of the set \(Y\), it was forced on us once the first instantiation had been made. So the whole proof came to seem natural and inevitable, rather than involving a little piece of magic.</p>
