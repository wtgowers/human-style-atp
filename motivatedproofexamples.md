---
layout: page
title: Examples of motivated proofs
description:
background: '/img/maths_background.png'
mathjax: true
---

<h3>What you will find here</h3>

<p>This page will mostly consist of links to files that contain examples that people have come up with of proofs (or more precisely proof write-ups) that we would like to count as "motivated". Informally, this means that it is clear where every proof step has come from. In particular, if an existential statement is to be proved, or a universally quantified statement is to be instantiated, it is not enough simply to substitute in an expression that works: the expression has to emerge as a "solution", often as a result of the problem being "reduced" to something significantly simpler.</p>

<p>As explained <a href="{{site.baseurl}}/motivatedproofs.html">in the parent page to this one</a>, we hope eventually to develop a formal definition of a "motivated proof". One of the reasons for creating a repository of examples is to help to narrow down what such a definition might look like.</p>

<h3>An example</h3>

<p>We illustrate this with a simple but non-trivial example: that of proving Cantor's famous theorem that there is no surjection from a set $X$ to its power set $\mathbb P X$. In order to prove this, it is sufficient to take an arbitrary function $f:X\to\mathbb P X$ and exhibit a subset of $X$ that does not belong to the image of $f$. The usual "unmotivated" approach to this is simply to write, "Consider the subset $Y=\{x\in X: x\notin f(x)\}$ of $X$," and then to proceed with the simple proof that shows that $Y$ has no preimage under $f$. We regard this as unmotivated because the definition of the set $Y$ comes out of nowhere and "just happens to work".</p>

<p>A motivated presentation of the same proof can be given as follows. Instead of saying what $Y$ is, we treat it as an unknown that we have to "solve for". So $Y$ is a subset of $X$ and we need the statement $f(y)=Y$ to lead to a contradiction. Using the definition of set equality, we find that we want to derive a contradiction from the statement $\forall x\ x\in f(y)\iff x\in Y$. For that it is sufficient to choose a value of $x$ that will lead to a contradiction. But there is only one element of $X$ that has been mentioned, namely $y$, so let us try to derive a contradiction from the statement $y\in f(y)\iff y\in Y$. Since we know nothing about $y$, we shall need $Y$ to have the property that $y\notin Y$ whenever $y\in f(y)$ and $y\in Y$ whenever $y\notin f(y)$. In other words, we shall have to take $Y$ to be $\{y\in X:y\notin f(y)\}$. Taking that set, we have the desired contradiction.</p>

<p>In the second presentation, we did instantiate a quantifier when we chose to set $x$ to equal $y$. But that choice did not come out of nowhere, as $y$ was very much present in the problem -- indeed, as commented, it was the only element of $X$ that had been mentioned. As for the definition of the set $Y$, it was forced on us once the first instantiation had been made. So the whole proof came to seem natural and inevitable, rather than involving a little piece of magic.</p>

<p>We stress that just as a statement can have more than one proof, so a proof can have more than one motivation. For example here, a motivation that probably reflects better how the result was actually discovered would be to start with a (motivated!) proof of Cantor's diagonal argument in one of its standard formulations and then to generalize it until one arrives at the result above.</p> 

<h3>Some attempts at motivated proofs</h3>

<p>We do not yet have a formal definition of a motivated proof. The links here are to files that contain "attempted motivated proofs" in the following sense: they are presentations of proofs that aim to be easily convertible into motivated proofs in a more formal sense if we do manage to come up with an adequate definition. Not all of them are complete, but the failed attempts may still be interesting and may provoke more successful ones. We have experimented with different modes of presentation, and do not claim to have found an optimal one. We welcome feedback on these attempts. Also, if you think you can write a similar presentation of a proof for which some non-trivial "rabbit" is customarily used, then we would be very happy to include a link to it on this page (possibly after a bit of feedback and modification, just to make sure that it is indeed an example of what we are trying to do).</p>

<p><a href="https://drive.google.com/file/d/1HYN2TqQG-8RP52OXl7lAeaLwb7qfMTW6/view?usp=sharing" target="_blank">Three questions from a sheet of discrete mathematics exercises for computer scientists at Cambridge.</a> The proofs are interspersed with comments in red that explain the motivation for each step.</p>

<p><a href="https://drive.google.com/file/d/12IQIhjIY-5_x8iOJlpiSh7PiqqxNftnC/view?usp=sharing" target="_blank">A question about Fibonacci numbers, also from a sheet of discrete mathematics exercises for computer scientists at Cambridge.</a> The proof steps are presented in one column with motivating comments next to them in another column.</p>

<p><a href="https://drive.google.com/file/d/17Q7uOoduRnLbLceohRxTZelmRuxD7zb_/view?usp=sharing" target="_blank">A question from the same source about a Collatz-like sequence.</a> The question is solved, but the motivation for the solution is incomplete. This time proof steps are numbered, and after each one there is a comment in red about the motivation. This format seems to strike quite a good balance between the labour of typesetting and the clarity of the result.</p>

<p><a href="https://drive.google.com/file/d/1ZFPzJeMCASqYZFItzi9t2_lznSslm3QG/view?usp=sharing" target="_blank">A set-theoretic question from the same source.</a> Numbered steps with red comments about motivation.</p>
  
<p><a href="https://drive.google.com/file/d/1ysJe4UZW9AikYrYVETPXXPOuOQlrp6ya/view?usp=sharing" target="_blank">A motivation for the idea of completing the square.</a> Numbered steps with red comments. Some green comments too to indicate issues that need more thought.</p>

<p><a href="https://drive.google.com/file/d/187XcVlGfX4_1PT1h_4fMwvC_dGDo-ckk/view?usp=sharing" target="_blank">A 3-regular graph cannot have nine vertices.</a> This is done in 94 numbered steps with red comments about motivation. (The challenge is to "generate" the idea of considering the parity of the sum of the degrees rather than just to exhibit it. However, there may well be shorter routes.)</p>

<p><a href="https://drive.google.com/file/d/15Jk0vJ5VW2_MIai_9BOJtWa7NP0T_V9O/view?usp=sharing" target="_blank">Lagrange's theorem (about subgroups).</a> Numbered steps with red comments.</p>

<p><a href="https://drive.google.com/file/d/1ZLO_8Q7EDneZm9sZxLX4bdH8-DpKxhoU/view?usp=sharing" target="_blank">A sequence that is unbounded above has a subsequence that tends to infinity.</a> Numbered steps. This turned out to be surprisingly hard, and the file contains a few attempts at it.</p>

<p><a href="https://drive.google.com/file/d/1qL62Lay2k3-gT98VrEblfnvFkA8UaAW9/view?usp=sharing" target="_blank">Ramsey's theorem (for infinite graphs).</a> This is incomplete, and seems to be quite challenging. It is presented as a sequence of "tableaux" with explanations of how to get from each one to the next.</p>

<p><a href="https://drive.google.com/file/d/1VHFPUOCBAqpj57DJg9AkrgjrsjO53odd/view?usp=sharing" target="_blank">The irrationality of $\sqrt 2$.</a> Numbered steps with accompanying motivations (not in red this time).</p>

<p><a href="https://drive.google.com/file/d/1nKnQRhT6EaXK_fZhh6jgq5znRCx3mm03/view?usp=sharing" target="_blank">A uniform limit of continuous functions is continuous.</a> Numbered steps with accompanying motivations in red.</p>

<p><a href="https://drive.google.com/file/d/1rLni27-4n1u_vpsUaqZsZCMff5HKvvT5/view?usp=sharing" target="_blank">A question about sequences from a past Discrete Mathematics exam for Computer Science students.</a> Contains some interesting discussion about proving an expression is equal to 0 in a motivated way.</p>

<p><a href="https://drive.google.com/file/d/16NnFwTkUNQDkMw5niE5WAc7YS6A5xvj-/view?usp=sharing" target="_blank">A more challenging question from the same source.</a> There are several proofs presented, some being easier to motivate than others.</p>

<p><a href="https://drive.google.com/file/d/1iNRhDlgIzImipIEqD3v9Y4q6Fqo0A2Nu/view?usp=sharing" target="_blank">Some more questions from the same source.</a> This contains a couple of examples of symmetry-based reasoning, namely noticing that the problem has reduced to itself with different values, and using that as a motivation for doing a proof by induction.</p>

<p><a href="https://drive.google.com/file/d/1N7PiwUGW_K_uM46DLE4-DXDmp4xKcpom/view?usp=sharing" target="_blank">A motivated proof of Cantor's Diagonal argument.</a>Similar but not quite the same as the above</p>

<p><a href="https://drive.google.com/file/d/1eMA6DaWzLEPsQMoB8ipWWy4SzKKA609g/view?usp=sharing" target="_blank">A Compact subset of a Hausdorff space is closed.</a></p>

<p><a href="https://drive.google.com/file/d/1OxrT3y-9ewLg4_Lt0sVAhGcJrOLSn2Lo/view?usp=sharing" target="_blank">The closure of the interior of the closure of the interior is the same as the closure of the interior.</a> This motivated proof uses the idea of generalising a lemma.</p>

<p><a href="https://drive.google.com/file/d/1-oBfjbQ5PJN5klJUJXit_UCx3Bo8rmlC/view?usp=sharing" target="_blank">A continuous image of a compact set is compact.</a> This is a fairly detailed discussion of how a program ought to be able to solve this problem, highlighting the work that still needs to be done (as of early January 2023) before we actually have such a program.</p>

<p><a href="https://drive.google.com/file/d/1cbfCteaFU89rr3IxAr7ILQp-HqFKJDvT/view?usp=sharing" target="_blank">A closed subset of a compact topological space is compact.</a> This is similar in style and aims to the previous document. </p>
