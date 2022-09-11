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

At this stage we have three sets of type subset of $Y$, namely $f(\overline A)$, $f(A)$, and $\overline{f(A)}$. It's tempting to check each one to see whether it is closed, but that feels a bit too much like brute-force search, when two of the options are "silly" and shouldn't be considered. 

We could consider adding to the hypotheses the information that $\overline A$ and $\overline{f(A)}$ are closed. It's not clear to me whether that's a good idea: on the one hand, it seems like making observations for the sake of it, but on the other hand a human mathematician would be instantly aware that those two sets are closed.

A third possibility is to use the library result $f(E)\subset F\iff E\subset f^{-1}(F)$ to reformulate the target. That is quite a nice thing to do because it creates a set of the form $f^{-1}(B)$, thereby giving us another clue about how to instantiate $B$. 

I don't see a compelling reason to argue that the third approach is best, and I would be wary of just "observing" that that deduction creates a potentially useful term. Here's a case where it probably helps to think about subtasks rather than features. If we had a subtask "create a matching term of the form $f^{-1}(B)$" then we would be drawn to look for results that do not involve $f^{-1}$ on one side and do on the other. In that way we could pick out the appropriate result without trying all sorts of irrelevant and unhelpful results first. (But this does seem to be a potentially tricky place to get an algorithm to do the sensible thing.) 

Let's go ahead with the third approach and see where it takes us. Library modus tollens gives us this.

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
  \overline A\subset f^{-1}(\overline{f(A)})\\
  \hline
  \end{array}
  $$
</p>

At this point, instantiating $B$ becomes easy -- if we take $B=\overline{f(A)}$ we will create a matching $f^{-1}(\overline{f(A)})$, and if we check whether $\overline{f(A)}$ is closed, we see quickly that it is. How all that should be organized is not completely obvious -- do we observe that we get the match, decide to check whether the condition holds, create a very easy subproblem to do the check, solve the subproblem, thereby establishing that the 
condition does indeed hold, and finally do the instantiation? That feels like roughly what would go on instantaneously in my brain, but it's not completely obviously the best way of organizing an algorithm. But for now let's just jump to the conclusion of the instantiation.

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
  \text{is_closed}(f^{-1}(\overline{f(A)}),X)\\
  \hline
  \\
  \hline
  \overline A\subset f^{-1}(\overline{f(A)})\\
  \hline
  \end{array}
  $$
</p>

There is a library result that says that if $F$ is closed and $E\subset F$, then $\overline E\subset F$. (This is an almost instant consequence of the definition, but it is nice to have it stated as a separate fact.) Using this library result we can reduce the target as follows.

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
  \text{is_closed}(f^{-1}(\overline{f(A)}),X)\\
  \hline
  \\
  \hline
  A\subset f^{-1}(\overline{f(A)})\\
  \hline
  \end{array}
  $$
</p>

One option we have in front of us at this point is to use the result $f(E)\subset F\iff E\subset f^{-1}(F)$ again, but in the other direction. Something nice about it is that it creates a new match, giving us two occurrences of $f(A)$ in the same expression. That allows us to "quotient out" by the internal structure of $f(A)$, which plays no further role -- all we care about is that we've got some subset of $Y$.

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
  \text{is_closed}(f^{-1}(\overline{f(A)}),X)\\
  \hline
  \\
  \hline
  f(A)\subset\overline{f(A)}\\
  \hline
  \end{array}
  $$
</p>

And now we're done, by the library result that every set is contained in its closure (which again follows instantly from the definition, but I prefer to think about the closure abstractly: it is uniquely determined by the three properties $\text{is_closed}(\overline E)$, $E\subset\overline E$, and $E\subset F\ \wedge\ \text{is_closed}(F)\implies\overline E\subset F$. 

## Concluding remarks.

Although that went reasonably satisfactorily, there were a number of points where it wasn't obvious how a program would choose the right move to do and ignore multiple silly moves. So what was presented above feels for the moment more like a motivated proof than a justified proof -- for each move, one can explain why it is a good thing to do, but it's harder to explain in advance why it should be the top priority move when it is chosen.
