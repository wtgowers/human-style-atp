---
layout: page
title: Minutes
description:
background: '/img/maths_background.png'
mathjax: true
---
<!-- dropdown help from: https://gist.github.com/pierrejoubert73/902cc94d79424356a8d20be2b382e1ab -->
<!-- markdown help from: https://stackoverflow.com/questions/15917463/embedding-markdown-in-jekyll-html --> 
<div markdown="1">
This is a partial public record of what is discussed in our meetings, some of which will be face to face and others on Slack or Zoom. They are here partly to remind ourselves of avenues that we started exploring but temporarily abandoned, but more importantly as a way of being more inclusive to people who are participating remotely. (The only reason that it is partial is that we cannot guarantee that we will always get down to writing a summary of each meeting. Indeed, we have had a number of meetings that are not mentioned here.)

<details>
    <summary><b>Thursday 28th April 2022</b></summary>
    
### Thursday 28th April 2022
    
*Present (on Zoom): Katie Collins, Timothy Gowers, Angeliki Koutsoukou-Argyraki, Matei Mandache, Bhavik Mehta, Wills Wynn-Thomas.*

This was mainly an introductory meeting where those present got to know each other. Amongst the topics discussed were what our short-term targets might be, when we wanted to start in earnest, how an associated website might be designed and what platform it might run on, how best to organize ourselves to get the benefits of being a team, and what further skills we might be looking for when recruiting. The meeting took place half an hour or so after TG announced the project online.

Not too many firm conclusions were reached. Here are a few scattered thoughts that I (TG) remember a week later.

1. There was a fairly clear wish to get started as soon as possible, though some of us had other commitments that would for the time being limit the amount they could devote to the project. The level of activity is likely to increase significantly in September and then again from October.
2. There seemed to be general acceptance that a good short-term target would be to try to develop a platform that would make applying problem-transforming ``moves" easy and transparent, so that (i) people could play with it and (ii) people could design high-level programs for choosing which move to do when, with the implementation of the moves already taken care of. If we had such a platform, it could greatly facilitate, and therefore accelerate, later research.
3. It was felt that the approach we were likely to take was sufficiently different from the approaches taken in various formalization communities that it would be better to create such a platform from scratch than to write it on top of a prover such as Lean, Isabelle or Coq. (However, we would make the design public, to make it as easy as possible for anyone who wanted to build a similar platform in Lean, say.) 
4. The suggestion was made that Sledgehammer would be useful for identifying problems that are beyond the scope of current provers, to give us some challenges to work towards.
5. Github pages was suggested as a good platform for a website. It was felt that we might need various different kinds of page. For example, a wiki could be useful as a way of organizing what we had done so far, and helping others to join in at a later stage. Something like a blog could be good for shorter-term interactions. And it would be good to have repositories for things like attempts to find "fully motivated proofs" of theorems, bits of code, accounts of technical difficulties that are holding us up (that is, "open problems" but not in the usual mathematical sense), possible approaches to some of the theoretical questions, and so on.
</details> 

<details>
    <summary><b>Thursday 5th May, 2022</b></summary>

### Thursday 5th May 2022

*Present (on Zoom): Katie Collins, Timothy Gowers, Mateja Jamnik, Angeliki Koutsoukou-Argyraki, Matei Mandache, Bhavik Mehta, Wills Wynn-Thomas.*

I am writing this almost a week later, and have only a rather incomplete memory of the meeting. We welcomed Mateja Jamnik, who underlined the importance of having clear criteria for what would constitute success with the project. TG pointed out that this was partially addressed in the 54-page document accompanying the announcement of the project. However, the criteria there were focused mainly on extending the range of proofs that can be found without cheating, and while sufficient progress in that direction would certainly count as success, there are more theoretical goals that would do so as well, if attained, so further thought is needed here. 

TG reported on the reaction to the announcement a week earlier, including almost 30 expressions of interest from potential future participants. 

There was some discussion about what constitutes a motivated proof. MM reported on his attempts to find a motivated proof of the intermediate value theorem. He had found that the easiest approach to motivate was repeated bisection, but that it was difficult to justify completely the observation that the intersection of the intervals is a singleton -- where does the decision to look at the limit of the left end points come from? MJ pointed out that some of our ideas about motivated proofs and the relationship between move types and what is stored in the library resemble Alan Bundy's concept of proof planning. 

BM introduced a functional equation $f(x^3+y^3)=xf(x^2)+y^2f(y)$ (where $f:\mathbb R\to\mathbb R$) and some time was spent trying to find a motivated solution to it. We got as far as conjecturing, in a suitably motivated way, that the only solutions were of the form $f(x)=ax$. 

The website was again discussed but the discussion was rather brief and not much progress was made. However, KC had made useful suggestions during the preceding week: among the options considered (for very different purposes) were GitHub pages and Slack.
</details> 

<details>
    <summary><b>Thursday 12th May 2022</b></summary> 
    
### Thursday 12th May 2022

*Present (on Zoom): Katie Collins, Timothy Gowers, Angeliki Koutsoukou-Argyraki, Matei Mandache, Bhavik Mehta, Wills Wynn-Thomas. Apologies received from Mateja Jamnik.*

We started out by discussing what we wanted from a website. TG had sent round some ideas during the week. BM, KC and TG agreed to discuss it further, with MM also expressing an interest, and revealing that he had some knowledge of Javascript.

We spent a bit of time discussing what might go into the library of a theorem-proving program, the basic idea being that it should represent the "background knowledge" of a human mathematician who is solving a problem. What qualifies a statement to be "library-worthy", as opposed, say, to being a statement that one would expect to deduce quickly from library results? And how should the library be structured? Should it have a tree (or DAG) structure? Should there be tags to model associative memory? Should a useful special case of a general result be recorded separately? There are many questions like these.

AK-A told us about a project she is involved in called [concept-oriented search](https://behemoth.cl.cam.ac.uk/search).

We also discussed Monte-Carlo key search.

We discussed "noticing". For instance, what happens when it jumps out at us that the expansion of $(x+y)^3$ is relevant to a problem where it is not given to us directly?

We talked about post-mortems of proofs, which are important for human mathematicians but potentially quite challenging to program a computer to do. For example, if we are searching for a suitable inductive hypothesis, sometimes we try out a hypothesis that we do not expect to work, with a view to analysing why it doesn't work and strengthening it in a suitable way. As another example, sometimes to find a proof of a statement we try to prove the negation with a view to understanding why we have failed. 

AK-A mentioned Nitpick and Quickcheck, two counterexample-finding tools in Isabelle.

</details> 

<details> 
    <summary><b>Friday 20th May 2022</b></summary> 
    
### Friday 20th May 2022

*Present (in person, at different moments): Katie Collins, Timothy Gowers, Angeliki Kousoukou-Argyraki, Bhavik Mehta, Wills Wynn-Thomas.*

We met in person for the first time. In the late morning Katie Collins, Bhavik Mehta and Timothy Gowers mainly discussed technical details of the website. We then went to lunch in Churchill, where we had arranged to meet members of Larry Paulson's group. Wills Wynn-Thomas joined us there. After lunch, TG, BM and WW-T went back to CMS (the Centre for Mathematical Sciences) with Angeliki Koutsoukou-Argyraki, where for the first time we were able to have a mathematical discussion with the help of a whiteboard (and also a glass table top). We discussed how a proof of Ramsey's theorem might be generated using a finite set of moves, and also, following on from the discussion initiated by Matei Mandache two weeks earlier, how the proof of the intermediate value theorem that produces the rabbit $\sup\lbrace x\in\mathbb R: x^2<2\rbrace$ could be fully motivated. Some progress was made.

</details> 
    
<details> 
    <summary><b>Thursday 30th June 2022</b></summary> 
    
### Thursday 30th June 2022

*Present (on Zoom): Katie Collins, Timothy Gowers, Angeliki Kousoukou-Argyraki, Matei Mandache, Bhavik Mehta, Wills Wynn-Thomas.*

This is not the first meeting since 12th May, but the meetings since then have been on Slack, so we have complete transcripts of them. 

We discussed the current state of the website: the upshot of the discussion was that soon it will be ready to be populated, and that it is a realistic target to have a fairly complete initial website by the end of July.

TG gave an update on recruits: one postdoc is due to start in October and two PhD students in January.

We discussed where we felt we had got to with defining move types. There is work needed to define individual move types more precisely, which also requires us to pin down what precisely is being ``moved", so there was some discussion about how we should define what a problem state is. It seemed like a realistic target to come up with a satisfactory notion of problem state by the end of the month, and to have a program that could implement at least some move types (but not necessarily with a nice interface). By the end of September, it might be reasonable to hope for more: a system that would allow us to implement all the move types that we have come up with so far, and moreover a system that would be readily extendable. Ideally the interface would be nice enough to be convenient to use even if it wasn't all that pretty.

</details>
    
<details> 
    <summary><b>Thursday 7th July 2022</b></summary> 
    
### Thursday 7th July 2022

*Present (on Zoom): Timothy Gowers, Angeliki Kousoukou-Argyraki, Matei Mandache, Bhavik Mehta, Wills Wynn-Thomas. Apologies received from Katie Collins.*

We discussed whether it would be desirable to switch for a while from our current focus on theoretical questions (and in particular the question of pinning down a good notion of "motivated proof") to trying to design and implement an algorithm. The aim in the latter case would be to produce a program that was capable of solving problems that ROBOT had been unable to solve, and more generally to set ourselves a benchmark by seeing what we were able to achieve in a relatively short time before the project started in earnest in October.
    
The general feeling was that this would be a good idea. Of course, it raised subsidiary questions. One was what problems we would like the program to solve that ROBOT did not solve. TG is keen on trying to get a program that can prove that a uniform limit of continuous functions is continuous, which he judges to be an ambitious but not unrealistic target. It would also be good to try to identify problems that are just beyond what ROBOT could do -- one such example is to prove that if f is an injection then f(A cap B) = f(A) cap f(B).
    
AK-A brought up the question of how we wanted to go about populating the library that the program would draw on, making the suggestion that we might like to take an existing library and modify it for our purposes (which would include leaving out several of its statements, and also imposing some kind of partial order on the results). TG raised the issue that the way results are stated in textbooks is often not the way we use them in context: for example, if we see that d(x,y) < a and d(y,z) < b, we will typically go in one step to d(x,z) < a + b. So we may want several different formulations of key results so that the program doesn't have to keep working out the simple equivalences. 
    
It was agreed that at this stage the most efficient way to get a program up and running would be for those interested in programming to work closely together.
    
 </details>
    
 <details> 
    <summary><b>Friday 16th September 2022</b></summary> 
    
### Friday 16th September 2022

*Present (on a Slack huddle): Timothy Gowers, Angeliki Kousoukou-Argyraki, Wills Wynn-Thomas.*

This was a meeting with just a few of us to discuss the structure and content of the library.
    
From what I remember, the bulk of the discussion ended up being looking at the HOL library and thinking about which results in it would be appropriate ones to include in our library and which wouldn't. We found examples of both, and thought about what the distinction was.
 
One example was the result   (succ x - y) - succ z = (x - y) - z.  I was fairly convinced that that should not be in our library, but what was the reason? Of course, it can be easily deduced from other results, but that is not a sufficient condition for excluding it, since if we include simple consequences of results, then it can make searching for matches much easier. (I'm thinking of things like versions of the triangle inequality such as $d(y,z) \leq d(x,y) + d(x,z)$ that are there to save us from having to use symmetry, or statements like $a + b - a = b$ that avoid the need to use commutativity and the definition of additive inverses.) In the end, what seems inappropriate about the above result is that it would not be used in a normal mathematical context or in a low-level context. To elaborate, if we are reasoning in the integers, we typically use properties of addition, subtraction, multiplication, etc., and we use them directly, so we never even write down an expression that involves the successor function. If on the other hand we wish to prove something like the associativity of addition using the Peano axioms, then we will use the successor function, but then it will be a low-level proof, so we would normally expect to work from the axioms, rather than using lots of statements like the one above. (More precisely, we would probably prove a sequence of basic facts, and each result in that sequence would make use of earlier results.)

Another example was a result in a section on Euclidean spaces, which said that if $u_1,...,u_n$ is an orthonormal basis and $|<x,u_i>| \leq |<y,u_i>|$ for every $i$, then $||x|| \leq ||y||$. It seems to me that if our target was to prove that $||x|| \leq ||y||$, then we wouldn't immediately go and search for tools such as the above, and see whether they work. Rather, we (by "we" I mean humans here) would tend to know that it's probably easier to square both sides, and if there was a handy basis around, then we might well change the target to $\sum_i<x,u_i>^2 \leq \sum_i<y,u_i>^2$. At that point, if there was some reason to think that the hypotheses might be satisfied, we could consider using the rule that if $a_i \leq b_i$ for every $i$, then $\sum_i a_i \leq sum_i b_i$. That last result is in the HOL library too, but it seems more natural to me. So for some reason my instinct here is that the program should be expected to reduce the inner product statement to the more basic statement about real numbers. And I think that's borne out by what a human mathematician would say if challenged: the reason that $||x|| \leq ||u||$ would be that if every coordinate of $x$ w.r.t. the basis is at most the corresponding coordinate of $y$ w.r.t. the basis, then when you add up the squares of the coordinates of $x$ you get at most what you get for $y$ (silently using the fact that $x^2$ is an increasing function on the non-negative reals). I don't think anyone would appeal to the principle that if you increase the sizes of each coordinate then you increase the norm.
    
Even with the real-numbers result, I don't think if we want to prove that one sum is smaller than another sum that we should instantly reach for a result like that in the library, since very often its hypotheses won't be satisfied. But that's not really a question about the content of the library, so much as how library reasoning should work.

We also discussed the content of a library about Zorn's lemma and related results. We would surely want all three of AC, Zorn and the well-ordering principle in the library, because mathematicians make use of all three in proofs -- which equivalent statement is most convenient to use varies from problem to problem. But the library also contains a lot of lemmas about chains, maximal elements, etc. For instance, it has a slightly strange definition of the "successor" of a chain, which is applied to all subsets of the set in which the chain lives (no doubt for technical reasons). It is defined to be the set itself if the set is not a chain or if it is a maximal chain. Otherwise, it is defined to be any chain that strictly contains the given chain. So it's not well defined. I'm not sure how Isabelle handles that, but probably just by treating this kind of successorship as a relation rather than as a function. Anyhow, this is building up to saying that there is a lemma that says that C is a subset of succ(C), which follows completely trivially from the definition. This morning my view was that that should not belong to the library, but now that I think about it again, I'm less sure -- one wouldn't want the poor old program to have to go through the trivial proof. But I'm not sure I would want the definition of succ(C) in the first place, which I think is probably there for the purposes of formalizing a slightly strange proof of Zorn's lemma.
    
As a first stab at a general principle, I'd say that the easy results we want to put in the library are those that we would expect to use silently in higher-level proofs. So a result like  succ(x) - succ(y) = x - y  would not be included, because I can't imagine any problem for which it would be appropriate to quote that: if the problem is at the level of arithmetic then I would never mention succ, and if it's at the level of the Peano axioms then I would expect to formulate and prove that result if I found it useful. By contrast, a result such as  $(x + y \leq z\ \wedge\ y \geq 0)  => x \leq z$  is something that represents the kind of "small jump" that one often sees in mathematical writing, so it would be reasonable to include that in the library.
    
We also discussed other examples of reformulating results to make it easier for a program to spot when they can be applied. One example is the mean value theorem. It is quite common for undergraduates to see the theorem in lectures but then not to notice that it is the tool to use when one wishes to prove statements such as that if $f$ is differentiable with strictly positive derivative then it is strictly increasing. However, if one were to present a reformulation that says "Let $f$ be differentiable with derivative that belongs to an interval $I$. Then $f(b)-f(a)\in(b-a)I$ for every $a,b$.", then it would be easier to spot that the mean value theorem was applicable: the hypothesis is of exactly the right form, and the conclusion quickly implies what we want. It will be interesting to think about whether this can always be done or whether for some results one needs a separate type of "how to use this result" entry in the library. The former would be preferable, but maybe it is too much to hope for.
    
</details>
 
 <details> 
    <summary><b>Friday 16th September 2022</b></summary> 
    
### Wednesday 21st September 2022

*Small in-person meeting with Katie Collins, Timothy Gowers, and Wills Wynn-Thomas.*

The main focus was going through (part of) the proof that a uniform limit of continuous functions is continuous. We agreed that nested boxes are the best way to handle statements with a more complex logical structure. But since that wasn't controversial, it wasn't the most interesting point. We also talked a bit about whether it's possible to use hypotheses instead of type declarations. WTG wondered whether there might be problems applying a result such as that if $a + c < b + c$ then $a < b$ (stated with the hypotheses that $a$, $b$ and $c$ are real, say) in a situation where we had terms such as $d(x,y)$. Where in a problem state would it say that $d(x,y)$ satisfies the hypothesis "is real"? Would we, for example, use the hypothesis that $X$ is a metric space to "deduce" (using library reasoning) that for every $u$, $v$ in $X$ we have $d(u,v)$ real? If we did that, would it be importantly different from what a type system would do less visibly? I don't know what I think about this.
We also discussed situations where we have a hypothesis such as
     
     $$ \forall \epsilon (\text{real}(\epsilon)\ \wedge\ \epsilon > 0) => ( \forall x\ x\in X\implies (P(x,epsilon) => Q(x,epsilon)) )$$

One approach to a hypothesis like this is to make epsilon a metavariable and add the statements $\text{real}(\epsilon)$  and  $\epsilon > 0$   as targets (done in such a way that it's clear what hypotheses we're allowed to use). It looks a bit strange to do this, as these targets are somehow not "substantive". But that seems to be a question of presentation/interfaces etc. and not really a question about how the program should work.
Another approach is simply to "carry around" the conditions  $\text{real}(\epsilon)$  and  $epsilon > 0$  as we go along, and reason with the "interesting" part of the hypothesis, knowing that at some stage we'll have to verify the conditions. This is similar in spirit to forming metavariables -- it's just that it's not the choice of epsilon that is being postponed (though that's true too) but the verification of some basic, and maybe sometimes less basic, conditions.

A technical point that came up is that the uniform convergence hypothesis is applied twice, to get that $f(x)$ is close to $f_n(x)$ and that $f(y)$ is close to $f_m(y)$, and it feels natural to use the same upper bound for both distances. But it also seems wrong to assume that when we use a universally quantified hypothesis more than once, then we should make the same substitutions both times. Indeed, we obviously won't do so for all variables, but I'm saying that we won't necessarily want to do so for any variables. So it feels safer to expect the program to choose different metavariables and identify them later if that seems appropriate (and indeed we end up wanting to identify n with m above). We didn't fully resolve this issue and I plan to work through the example by hand again to try to get an idea of how it would work if we don't take the same small real number both times.
    
 </details>
 </div> 
