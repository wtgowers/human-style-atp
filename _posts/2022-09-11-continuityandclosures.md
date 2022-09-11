---
layout: post
title: "A problem about continuity and closures"
subtitle: "What to do when a waterfall architecture is insufficient"
date: 2022-09-09 17:00:00
background: '/img/maths_background.png'
author: "Timothy Gowers"
mathjax: true
---

This post is not yet finished.

## Statement of the problem.

In <a href="{{site.baseurl}}/2022/09/09/subtasks.html">the previous post</a>, which I recommend reading before this one, as much of it is relevant to this post and I don't plan to repeat that material here, I used as an example the problem of showing that if $X$ and $Y$ are topological spaces and $f:X\to Y$, then $f$ is continuous if it satisfies the property that $f(\overline A)\subset\overline{f(A)}$ for every subset $A$ of $X$. This implication is in fact an equivalence, so in this post I shall discuss how a program might discover a proof of the reverse implication, namely the following statement.

**Proposition.** *Let* $X$ *and* $Y$ *be topological spaces and let* $f:X\to Y$ *be continuous. Then* $f(\overline A)\subset\overline{f(A)}$ *for every subset* $A$ *of* $X$.

Here is an initial problem state.

<p>
  $$
  \begin{array}
  \hline
  X: \text{topological space}\\
  Y: \text{topological space}\\
  f:X\to Y\\
  A: \text{subset of }X\\
  \hline
  \\
  \hline
  \text{is_continuous}(f)\\
  \hline
  \\
  \hline
  f(\overline A)\subset\overline{f(A)}\\
  \hline
  \end{array}
  $$
</p>

We could at this point expand the subset relation in the target, but that will take the problem to a lower level than if we expand the definition of continuity. Perhaps a better argument, as it does not require making sense of the concept of "lower level" is to observe that if we expand the continuity definition, we obtain information about subsets of $Y$, which is potentially helpful for proving the target. (Here I'm assuming that the program would have a built-in type system that would be aware that, e.g., $f(\overline A)$ is a subset of $Y$.) As with the implication in the other direction, the closed-sets expansion of continuity is a good thing to try, because the target concerns closures, which are directly related to closed sets.

<p>
  $$
  \begin{array}
  \hline
  X: \text{topological space}\\
  Y: \text{topological space}\\
  f:X\to Y\\
  A: \text{subset of }X\\
  \hline
  \\
  \hline
  \forall B\subset Y\ \text{is_closed}(B,Y)\implies\text{is_closed}(f^{-1}(B),X)\\
  \hline
  \\
  \hline
  f(\overline A)\subset\overline{f(A)}\\
  \hline
  \end{array}
  $$
</p>
