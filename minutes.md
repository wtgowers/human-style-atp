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
    
<!-- ### Thursday 28th April 2022 -->
    
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

<!-- ### Thursday 5th May 2022 -->

*Present (on Zoom): Katie Collins, Timothy Gowers, Mateja Jamnik, Angeliki Koutsoukou-Argyraki, Matei Mandache, Bhavik Mehta, Wills Wynn-Thomas.*

I am writing this almost a week later, and have only a rather incomplete memory of the meeting. We welcomed Mateja Jamnik, who underlined the importance of having clear criteria for what would constitute success with the project. TG pointed out that this was partially addressed in the 54-page document accompanying the announcement of the project. However, the criteria there were focused mainly on extending the range of proofs that can be found without cheating, and while sufficient progress in that direction would certainly count as success, there are more theoretical goals that would do so as well, if attained, so further thought is needed here. 

TG reported on the reaction to the announcement a week earlier, including almost 30 expressions of interest from potential future participants. 

There was some discussion about what constitutes a motivated proof. MM reported on his attempts to find a motivated proof of the intermediate value theorem. He had found that the easiest approach to motivate was repeated bisection, but that it was difficult to justify completely the observation that the intersection of the intervals is a singleton -- where does the decision to look at the limit of the left end points come from? MJ pointed out that some of our ideas about motivated proofs and the relationship between move types and what is stored in the library resemble Alan Bundy's concept of proof planning. 

BM introduced a functional equation $f(x^3+y^3)=xf(x^2)+y^2f(y)$ (where $f:\mathbb R\to\mathbb R$) and some time was spent trying to find a motivated solution to it. We got as far as conjecturing, in a suitably motivated way, that the only solutions were of the form $f(x)=ax$. 

The website was again discussed but the discussion was rather brief and not much progress was made. However, KC had made useful suggestions during the preceding week: among the options considered (for very different purposes) were GitHub pages and Slack.
</details> 

<details>
    <summary><b>Thursday 12th May 2022</b></summary> 
    
<!-- ### Thursday 12th May 2022 -->

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
    
<!-- ### Friday 20th May 2022 -->

*Present (in person, at different moments): Katie Collins, Timothy Gowers, Angeliki Kousoukou-Argyraki, Bhavik Mehta, Wills Wynn-Thomas.*

We met in person for the first time. In the late morning Katie Collins, Bhavik Mehta and Timothy Gowers mainly discussed technical details of the website. We then went to lunch in Churchill, where we had arranged to meet members of Larry Paulson's group. Wills Wynn-Thomas joined us there. After lunch, TG, BM and WW-T went back to CMS (the Centre for Mathematical Sciences) with Angeliki Koutsoukou-Argyraki, where for the first time we were able to have a mathematical discussion with the help of a whiteboard (and also a glass table top). We discussed how a proof of Ramsey's theorem might be generated using a finite set of moves, and also, following on from the discussion initiated by Matei Mandache two weeks earlier, how the proof of the intermediate value theorem that produces the rabbit $\sup\lbrace x\in\mathbb R: x^2<2\rbrace$ could be fully motivated. Some progress was made.

</details> 
    
<details> 
    <summary><b>Thursday 30th June 2022</b></summary> 
    
<!-- ### Thursday 30th June 2022 -->

*Present (on Zoom): Katie Collins, Timothy Gowers, Angeliki Kousoukou-Argyraki, Matei Mandache, Bhavik Mehta, Wills Wynn-Thomas.*

This is not the first meeting since 12th May, but the meetings since then have been on Slack, so we have complete transcripts of them. 

We discussed the current state of the website: the upshot of the discussion was that soon it will be ready to be populated, and that it is a realistic target to have a fairly complete initial website by the end of July.

TG gave an update on recruits: one postdoc is due to start in October and two PhD students in January.

We discussed where we felt we had got to with defining move types. There is work needed to define individual move types more precisely, which also requires us to pin down what precisely is being ``moved", so there was some discussion about how we should define what a problem state is. It seemed like a realistic target to come up with a satisfactory notion of problem state by the end of the month, and to have a program that could implement at least some move types (but not necessarily with a nice interface). By the end of September, it might be reasonable to hope for more: a system that would allow us to implement all the move types that we have come up with so far, and moreover a system that would be readily extendable. Ideally the interface would be nice enough to be convenient to use even if it wasn't all that pretty.

</details>
    
<details> 
    <summary><b>Thursday 7th July 2022</b></summary> 
    
<!-- ### Thursday 7th July 2022 -->

*Present (on Zoom): Timothy Gowers, Angeliki Kousoukou-Argyraki, Matei Mandache, Bhavik Mehta, Wills Wynn-Thomas. Apologies received from Katie Collins.*

We discussed whether it would be desirable to switch for a while from our current focus on theoretical questions (and in particular the question of pinning down a good notion of "motivated proof") to trying to design and implement an algorithm. The aim in the latter case would be to produce a program that was capable of solving problems that ROBOT had been unable to solve, and more generally to set ourselves a benchmark by seeing what we were able to achieve in a relatively short time before the project started in earnest in October.
    
The general feeling was that this would be a good idea. Of course, it raised subsidiary questions. One was what problems we would like the program to solve that ROBOT did not solve. TG is keen on trying to get a program that can prove that a uniform limit of continuous functions is continuous, which he judges to be an ambitious but not unrealistic target. It would also be good to try to identify problems that are just beyond what ROBOT could do -- one such example is to prove that if f is an injection then f(A cap B) = f(A) cap f(B).
    
AK-A brought up the question of how we wanted to go about populating the library that the program would draw on, making the suggestion that we might like to take an existing library and modify it for our purposes (which would include leaving out several of its statements, and also imposing some kind of partial order on the results). TG raised the issue that the way results are stated in textbooks is often not the way we use them in context: for example, if we see that d(x,y) < a and d(y,z) < b, we will typically go in one step to d(x,z) < a + b. So we may want several different formulations of key results so that the program doesn't have to keep working out the simple equivalences. 
    
It was agreed that at this stage the most efficient way to get a program up and running would be for those interested in programming to work closely together.
    
 </details>
    
 <details> 
    <summary><b>Friday 16th September 2022</b></summary> 
    
<!-- ### Friday 16th September 2022 -->

*Present (on a Slack huddle): Timothy Gowers, Angeliki Kousoukou-Argyraki, Wills Wynn-Thomas.*

This was a meeting with just a few of us to discuss the structure and content of the library.
    
From what I remember, the bulk of the discussion ended up being looking at the HOL library and thinking about which results in it would be appropriate ones to include in our library and which wouldn't. We found examples of both, and thought about what the distinction was.
 
One example was the result   (succ x - y) - succ z = (x - y) - z.  I was fairly convinced that that should not be in our library, but what was the reason? Of course, it can be easily deduced from other results, but that is not a sufficient condition for excluding it, since if we include simple consequences of results, then it can make searching for matches much easier. (I'm thinking of things like versions of the triangle inequality such as $d(y,z) \leq d(x,y) + d(x,z)$ that are there to save us from having to use symmetry, or statements like $a + b - a = b$ that avoid the need to use commutativity and the definition of additive inverses.) In the end, what seems inappropriate about the above result is that it would not be used in a normal mathematical context or in a low-level context. To elaborate, if we are reasoning in the integers, we typically use properties of addition, subtraction, multiplication, etc., and we use them directly, so we never even write down an expression that involves the successor function. If on the other hand we wish to prove something like the associativity of addition using the Peano axioms, then we will use the successor function, but then it will be a low-level proof, so we would normally expect to work from the axioms, rather than using lots of statements like the one above. (More precisely, we would probably prove a sequence of basic facts, and each result in that sequence would make use of earlier results.)

Another example was a result in a section on Euclidean spaces, which said that if $u_1,...,u_n$ is an orthonormal basis and $|<x,u_i>| \leq |<y,u_i>|$ for every $i$, then $||x|| \leq ||y||$. It seems to me that if our target was to prove that $||x|| \leq ||y||$, then we wouldn't immediately go and search for tools such as the above, and see whether they work. Rather, we (by "we" I mean humans here) would tend to know that it's probably easier to square both sides, and if there was a handy basis around, then we might well change the target to $\sum_i<x,u_i>^2 \leq \sum_i<y,u_i>^2$. At that point, if there was some reason to think that the hypotheses might be satisfied, we could consider using the rule that if $a_i \leq b_i$ for every $i$, then $\sum_i a_i \leq \sum_i b_i$. That last result is in the HOL library too, but it seems more natural to me. So for some reason my instinct here is that the program should be expected to reduce the inner product statement to the more basic statement about real numbers. And I think that's borne out by what a human mathematician would say if challenged: the reason that $||x|| \leq ||u||$ would be that if every coordinate of $x$ w.r.t. the basis is at most the corresponding coordinate of $y$ w.r.t. the basis, then when you add up the squares of the coordinates of $x$ you get at most what you get for $y$ (silently using the fact that $x^2$ is an increasing function on the non-negative reals). I don't think anyone would appeal to the principle that if you increase the sizes of each coordinate then you increase the norm.
    
Even with the real-numbers result, I don't think if we want to prove that one sum is smaller than another sum that we should instantly reach for a result like that in the library, since very often its hypotheses won't be satisfied. But that's not really a question about the content of the library, so much as how library reasoning should work.

We also discussed the content of a library about Zorn's lemma and related results. We would surely want all three of AC, Zorn and the well-ordering principle in the library, because mathematicians make use of all three in proofs -- which equivalent statement is most convenient to use varies from problem to problem. But the library also contains a lot of lemmas about chains, maximal elements, etc. For instance, it has a slightly strange definition of the "successor" of a chain, which is applied to all subsets of the set in which the chain lives (no doubt for technical reasons). It is defined to be the set itself if the set is not a chain or if it is a maximal chain. Otherwise, it is defined to be any chain that strictly contains the given chain. So it's not well defined. I'm not sure how Isabelle handles that, but probably just by treating this kind of successorship as a relation rather than as a function. Anyhow, this is building up to saying that there is a lemma that says that C is a subset of succ(C), which follows completely trivially from the definition. This morning my view was that that should not belong to the library, but now that I think about it again, I'm less sure -- one wouldn't want the poor old program to have to go through the trivial proof. But I'm not sure I would want the definition of succ(C) in the first place, which I think is probably there for the purposes of formalizing a slightly strange proof of Zorn's lemma.
    
As a first stab at a general principle, I'd say that the easy results we want to put in the library are those that we would expect to use silently in higher-level proofs. So a result like  succ(x) - succ(y) = x - y  would not be included, because I can't imagine any problem for which it would be appropriate to quote that: if the problem is at the level of arithmetic then I would never mention succ, and if it's at the level of the Peano axioms then I would expect to formulate and prove that result if I found it useful. By contrast, a result such as  $(x + y \leq z\ \wedge\ y \geq 0)  => x \leq z$  is something that represents the kind of "small jump" that one often sees in mathematical writing, so it would be reasonable to include that in the library.
    
We also discussed other examples of reformulating results to make it easier for a program to spot when they can be applied. One example is the mean value theorem. It is quite common for undergraduates to see the theorem in lectures but then not to notice that it is the tool to use when one wishes to prove statements such as that if $f$ is differentiable with strictly positive derivative then it is strictly increasing. However, if one were to present a reformulation that says "Let $f$ be differentiable with derivative that belongs to an interval $I$. Then $f(b)-f(a)\in(b-a)I$ for every $a,b$.", then it would be easier to spot that the mean value theorem was applicable: the hypothesis is of exactly the right form, and the conclusion quickly implies what we want. It will be interesting to think about whether this can always be done or whether for some results one needs a separate type of "how to use this result" entry in the library. The former would be preferable, but maybe it is too much to hope for.
    
</details>
 
 <details> 
    <summary><b>Wednesday 21st September 2022</b></summary> 
    
<!-- ### Wednesday 21st September 2022 -->

*Small in-person meeting with Katie Collins, Timothy Gowers, and Wills Wynn-Thomas.*

The main focus was going through (part of) the proof that a uniform limit of continuous functions is continuous. We agreed that nested boxes are the best way to handle statements with a more complex logical structure. But since that wasn't controversial, it wasn't the most interesting point. We also talked a bit about whether it's possible to use hypotheses instead of type declarations. WTG wondered whether there might be problems applying a result such as that if $a + c < b + c$ then $a < b$ (stated with the hypotheses that $a$, $b$ and $c$ are real, say) in a situation where we had terms such as $d(x,y)$. Where in a problem state would it say that $d(x,y)$ satisfies the hypothesis "is real"? Would we, for example, use the hypothesis that $X$ is a metric space to "deduce" (using library reasoning) that for every $u$, $v$ in $X$ we have $d(u,v)$ real? If we did that, would it be importantly different from what a type system would do less visibly? I don't know what I think about this.
We also discussed situations where we have a hypothesis such as
     
$$ 
\forall \epsilon (\text{real}(\epsilon)\ \wedge\ \epsilon > 0) => ( \forall x\ x\in X\implies (P(x,\epsilon) => Q(x,\epsilon)) )
$$

One approach to a hypothesis like this is to make $\epsilon$ a metavariable and add the statements $\text{real}(\epsilon)$  and  $\epsilon > 0$   as targets (done in such a way that it's clear what hypotheses we're allowed to use). It looks a bit strange to do this, as these targets are somehow not "substantive". But that seems to be a question of presentation/interfaces etc. and not really a question about how the program should work.
Another approach is simply to "carry around" the conditions  $\text{real}(\epsilon)$  and  $\epsilon > 0$  as we go along, and reason with the "interesting" part of the hypothesis, knowing that at some stage we'll have to verify the conditions. This is similar in spirit to forming metavariables -- it's just that it's not the choice of epsilon that is being postponed (though that's true too) but the verification of some basic, and maybe sometimes less basic, conditions.

A technical point that came up is that the uniform convergence hypothesis is applied twice, to get that $f(x)$ is close to $f_n(x)$ and that $f(y)$ is close to $f_m(y)$, and it feels natural to use the same upper bound for both distances. But it also seems wrong to assume that when we use a universally quantified hypothesis more than once, then we should make the same substitutions both times. Indeed, we obviously won't do so for all variables, but I'm saying that we won't necessarily want to do so for any variables. So it feels safer to expect the program to choose different metavariables and identify them later if that seems appropriate (and indeed we end up wanting to identify n with m above). We didn't fully resolve this issue and WTG plans to work through the example by hand again to try to get an idea of how it would work if we don't take the same small real number both times.
     
We also briefly discussed how we wanted to handle OR statements in a tableau, which is not completely straightforward, since most of the nice options were taken up by the proposed notation for AND statements. Since an OR statement is logically equivalent to an implication, and since implications lead to various complications, it is not too surprising that OR statements are complicated too.

Another question that came up concerned peeling. If we have a box within a box, and in the smaller box is a quantifier, we can either peel it to just outside the smaller box or to right outside the whole thing. Which do we want to do? We'll need to look at some examples to decide on this. Logically this is starting with a statement such as $P\implies(Q\implies\forall x\ R(x))$ and deciding whether we want to change it to $P\implies\forall x\ Q\implies R(x)$ or to $\forall x\ P\implies(Q\implies R(x))$. The answer will certainly *sometimes* be the second option. The question is whether there are contexts for which the first option is preferable.
    
 </details>
    
 <details> 
    <summary><b>Monday 26th September 2022</b></summary> 
    
<!-- ### Monday 26th September 2022 -->

*Slack huddle with Katie Collins, Timothy Gowers, Angeliki Koutsoukou-Argyraki and Wills Wynn-Thomas, with Bill Hart attending in an unofficial capacity.* 

<p>The informal agenda of the meeting was effectively set in a Slack comment of Wills Wynn-Thomas, who wanted to talk about three "attackable issues", as he called them, that have arisen during his work on creating a first program. They are the nature of the library and how it should be searched, how the program should cope with easy existence problems (such as finding two positive numbers that add up to at most a given positive number), and what we should do about types.</p>
     
Before we got on to discussing those issues, WWT showed us the current state of the interface he is building, and the main thing the other participants took away from the meeting was how attractive it was. At the moment it lacks a lot of functionality that we would eventually want -- in particular, it has no automation, and although the user can choose some moves by simply clicking on appropriate buttons, some of them have to be typed in, and library search has to be done by had, also with typing in. However, there is every reason to think that these deficiencies will be remedied soon, and in the meantime the display of problem states and the implementation of moves that have been implemented are very impressive and a shot in the arm for the project. The interface is web based, so once it is sufficiently easy to use, we will think about deploying it publicly.
     
We reached a plan for starting the library, which was for AKA to create a document and fill it with a few results, for the rest of us to look at it and comment on the choice of results and the format in which they are entered, and once we reach some agreement about the content and format, for us to try to get quickly to a fairly substantial library, probably with AKA leading the effort but with others able to contribute to it. There was some discussion about how the library should be organized. WTG expressed the hope that its contents would not have to be categorized by hand, and that the program's search methods would automatically pick out suitable results. AKA pointed out that some categorization is important to make the library convenient for humans to browse (not for the purpose of solving problems, but for the purpose of evaluating the current state of the library). However, this categorization need not be used by the program. 
     
For the moment, the plan with easy existence problems is to have a repertoire of very easy problems -- ones that humans instantly know the answer to and that we don't want the program to have to keep on and on solving -- in the library, and for slightly harder existence problems to be solved by the program by means of metavariables and simplification of problem states. However, we are likely to have to revisit this question soon.
     
We agreed that it would be interesting to see how far we could get without an explicit type system. It's clear that we want the program to have some idea of types, so that it doesn't for instance see the statement 2+3=5 and consider trying to deduce from it that dim(5) is at most dim(2)+dim(3). This particular problem won't arise, as the program gives different names to different kinds of addition (in the background, though the interface will use the addition symbol for all of them). However, it may be that if we store results in the library with type declarations treated as hypotheses, then the program will simply not be able to make type errors of this kind unless its input already contains type errors.
</details>
    
<details> 
    <summary><b>Thursday 29th September 2022</b></summary>  
    
*In-person meeting with Katie Collins, Timothy Gowers, Bill Hart, Matei Mandache, and Wills Wynn Thomas*
    
After lunch with Larry Paulson's group, we had more of a work meeeting, mainly to discuss with Wills the next steps for the program. One suggestion was to introduce some very simple automation to it — e.g. a waterfall architecture that prompts the user when it finds more than one top-priority thing it can do. Another was that in the absence of a library, one could simply input the relevant library results (such as basic definitions) as hypotheses, which of course avoids the whole problem of library search but could still be interesting.
    
Bill raised an interesting point about whether making the library as efficiently searchable as possible for the program would conflict with making it conveniently searchable by humans — something we would want for the purposes of development. I don’t know whether we came to a firm conclusion on that question.
    
We also discussed what it would take to get the program to be able to solve easy algebra problems. Wills mentioned an example he had tried working through, which is to show that every element of a finite group has a non-trivial power equal to the identity. This appears to require an “idea” — to use the pigeonhole principle — which it is not immediately clear how to motivate, since the payoff doesn’t give you straight away a power of x equal to the identity, since you have to do the additional step of translating your two equal powers so that one of them becomes the identity. So what would prompt the program to use the pigeonhole principle in the first place?
    
After Katie and Tim had left, the meeting became a more technical one, mostly to go through the code written so far. There was a discussion also about whether we want the Haskell code for an interactive website to be run on a server (as it is at the moment) or to embed it into a Javascript program that executes on the client device. The consensus was that the latter would be preferable, due to security concerns and the risk of the server getting overloaded if there are too many requests.    
</details>
    
<details> 
    <summary><b>Tuesday 4th October 2022</b></summary>  
    
*In-person meeting with Michal Buran, Timothy Gowers, Bill Hart, Matei Mandache, and Wills Wynn Thomas*    
    
The main aim of the meeeting was to settle, if we could, on a format for library entries. We also had quite a detailed discussion about how a program could search the library without using brute force. Typically, a search will be for library results that have certain features, such as involving groups, or having a certain statement as a target (maybe only after some bound variables have been instantiated), etc. Probably we'll arrange the library in a way that makes it possible to do a tree search, or at least to narrow down the options a lot with a tree search, so that even if we resorted to brute force to do the rest, it would hardly matter from the point of view of running time (though we might want to be a bit subtler for theoretical reasons). 
    
We also considered the question of how much of a type system we would need, or how little we could get away with. The current plan is for equivalences to be stored in one way (the type conditions listed first and then a list of statements given that are equivalent under those conditions) and implications in another (all hypotheses, whether "substantive" or not, listed above the line, and conclusions below). WTG suggested a possible definition of a "non-substantive" hypothesis, as being one that one never actually proves except in the trivial way of matching it exactly with an assumption. So backwards reasoning that left a type hypothesis as an unmatched target would not be allowed. It may not be possible to detect this distinction automatically, but it would give a manual way of labelling type hypotheses when inputting library reuslts. 
    
We also had quite a lot of more speculative discussion, e.g. about how human memory works in a mathematical context and how we might try to model that. 
</details>
    
<details>
    <summary><b>Friday 7th October 2022</b></summary>
    
*In-person meeting with Michal Buran, Timothy Gowers, Bill Hart, Matei Mandache, and Wills Wynn Thomas*
    
A few hours before the meeting, MB sent a message to our Slack channel with some useful comments about the project. We discussed some of these. One was whether we were trying to model a "warts and all" human mathematician who tries silly things that don't work, learns from the experience, and eventually settles on a correct argument, or do we want more like a "superhuman" mathematician that almost magically chooses the best thing to try at each stage? TG suggested that maybe we want a superhuman mathematician for easy problems (a bit like a very experienced university professor dealing with routine questions from an undergraduate course), but that clearly there will come a point where we reach a plateau unless we allow quite a lot of backtracking. MB also expressed a worry that some of our motivated proofs were rational reconstructions after the event and that the true process of finding proofs is more messy. A third point was that maybe we are too optimistic about the general problem of extracting the right result from the library. A fourth, which we did not get round to discussing, was that there was a risk that we would overfit to a few problems unless we took steps to avoid that by feeding the program random problems that it had not seen before. And a fifth point was that it would be important to avoid "heuristic explosion": if we introduce too many heuristics to deal with difficulties as they arise, then we should make a serious effort to find deeper underlying principles that would allow us to reduce the number of them. 
    
Subtasks seem to be a good answer, at least in the short term, to some of these concerns, so we spent a while discussing them, and looking at how they can be used to solve a couple of problems. We decided that it was going to be hard to have a satisfactory library search procedure without using subtasks, so our immediate bottleneck is not in fact the lack of a library search procedure but rather the lack of a list of subtasks and features that would guide such a search. TG suggested that it would be good to have a clear separation in the program between the parts that recognise features and the parts that use that recognition to decide what moves to do. MM expressed keenness to start incorporating these aspects of the problem-solving process into the program. So all in all it became clear that settling on a good set of features/subtasks was a high priority. Another priority is to build up the library. TG showed some work he had done in that direction, focusing on definitions and results that would be useful for solving a topological-spaces problem that provides a characterization of continuous functions in terms of closures. The focus of his work was on the content of the library, but it should be fairly easy (if tedious) to rewrite the definitions and results he listed in the format we eventually decide on.
    
We discussed more general matters, such as how far we thought we would be able to go with basic moves and syntactic matching. The general view was that it could probably do some quite interesting things, but that eventually we would reach problems where more was needed. TG mentioned the problem of showing that a continuous function on [0,1] is bounded if one does not know the Heine-Borel theorem (or any other theorem related to compactness). The hard step for a program seems to be to get from observing that the function is locally bounded, which comes quite easily, to deciding to try to prove that [0,1] can be covered by finitely many of the intervals that show up in that statement. Once one has decided to prove that, finding the proof itself is not too bad, at least if one is familiar with "continuous induction". A possible route for a human would be to try to construct a locally bounded function on [0,1] that isn't bounded, and to notice what goes wrong. But that would be a step more sophisticated than anything that the "first generation" program we are currently planning could do. In general, a program that could attempt to prove the opposite of what it really wants to prove in order to learn from why it fails to do so would be powerful enough to solve some very interesting problems.
    
TG suggested an approach to the problem of showing that if $x$ is a nilpotent element of an algebra then $1+x$ is invertible. It is to decide first to build an element out of 1 and $x$, since that is all one is given, to note that the most general object one can build out of 1 and $x$ is a polynomial in $x$, to note that if $x^n=0$ then the degree of that polynomial is less than $n$, to write the polynomial out with its coefficients as metavariables, and then to solve the resulting equations for the coefficients, which is easy as they are in triangular form (this ends up just doing the polynomial long division). At the end one would observe that the extra $x^n$ that is left over is equal to zero so doesn't matter. Some scepticism was expressed that this was genuinely a "rabbit-free" presentation of the solution. (The challenging part might be the part where one reasons that it makes sense to go for a polynomial in $x$. We would want that to be a special case of a very general mode of reasoning rather than an ad hoc trick that was fed into the program.)
</details>
    
<details>
    <summary><b>Tuesday 11th October 2022</b></summary>
    
*In-person meeting with Michal Buran, Katie Collins, Timothy Gowers, Bill Hart, and Matei Mandache*
    
This was mostly a fairly chatty meeting about the longer-term future of the project.
</details>

<details>
    <summary><b>Friday 14th October 2022</b></summary>
    
*In-person meeting with Michal Buran, Timothy Gowers, Bill Hart, Matei Mandache, and Wills Wynn Thomas*    
    
The meeting started with MM describing a technical problem with the way the current program uses de Bruijn indices, which can result in it making mistakes when it expands definitions. The conclusion of the resulting discussion was that there were ways round this problem, though they might be a little tedious to implement.
    
Most of the meeting was spent going very carefully through the example of showing that an intersection of two open sets (in a metric space) is open. In a way this was a curious discussion to have, since the problem in question is one that ROBOT was able to do without difficulty. However, it did so by using a waterfall architecture of a kind that fails for other quite simple problems, so we wanted to find a different approach where "I can't find much else to do, so let's do this" would not count as a sufficiently good reason to do a move. 
   
The difficulties started from the very beginning. ROBOT's first move is to expand the target "$A\cap B$ is open" using the definition of open sets. But there is no obvious justification of this in terms of syntactic matching. Eventually we realized, thanks to a remark of MM, that subtasks could probably justify it, as follows. We would like to destroy the term $A\cap B$. One way to do that is to use the rule that $x\in A\cap B$ is equivalent to the conjuction of $x\in A$ and $x\in B$. That leads us to formulate a subsubtask -- that of creating the expression $x\in A\cap B$, which can be achieved in one move by expanding the definition of "is open". 

We then spent some time discussing why that particular subtask would be preferred over other "silly" subtasks, coming to the conclusion that it is probably unrealistic to hope for the program to keep zeroing in on the right thing to do, and that what we should be looking for instead is ruthlessly efficient pruning of very small search trees. So silly options might be considered, but they would be quickly rejected on the grounds that they are not "rewarded by something nice happening".  
    
The discussion continued in this vein, and while it did not lead to any attempt to design an actual algorithm, it did feel as though it was getting us closer to the point where we might want to try that.     
    
</details>    
    
<details>
    <summary><b>Tuesday 18th October 2022</b></summary>   
    
*In-person meeting with Timothy Gowers, Bill Hart, Matei Mandache and Wills Wynn-Thomas, with Katie Collins present via Zoom.*
    
This was one of our more informal chatty meetings, but it felt quite useful. We talked a little about algorithms for efficiently searching, including using hashes of hole expressions that had been substituted, whether we might use a balanced tree and how the search order would be given. (We are using the phrase "hole expression" to refer to a mathematical expression that has "holes" that can be filled in by terms of appropriate types. For example, if $X$ and $Y$ are given sets and $f:X\to Y$, we might write $f(\ )$ to mean $f$ evaluated at some element of $X$ that needs to be filled in -- that is, "placed in the hole".)  
    
</details>
    
<details>
    <summary><b>Friday 21st October 2022</b></summary>   
    
*In-person meeting with Timothy Gowers, Bill Hart and Matei Mandache*
    
MM reported that he had sorted out the difficulty with de Bruijn indices, so now the program correctly expands statements that involve quantifiers. 
    
The bulk of the meeting was taken up with a discussion of the moves needed to generate a proof that a compact subset of a Hausdorff topological space is closed. The aim was not to try to explain why a program would choose the moves, but just to understand the logic of the situation well enough to see which moves would be needed. As a result of working through the problem, three moves (or rather move types) were identified as ones that we probably need but do not yet have. 
    
The first was Skolemization. When we apply the Hausdorff condition, we have a point $x$ outside a compact set $A$ and for each $y\in A$ we find disjoint open sets $U(y)$ and $V(y)$ with $y\in U(y)$ and $x\in V(y)$. From the statement $\forall y\in A\ \exists U(y)\ \exists V(y) P(U(y),V(y))$ we then (as humans) do a kind of peeling of the existential quantifier, saying "For each $y$ let's take that $U(y)$." More formally, we convert the statement into $\exists U,V:A\to\tau\ \forall y\in A\ P(U(y),V(y))$. 
    
The passage from the first statement to the second relies on the axiom of choice, but many humans do it without even noticing that they are making infinitely many arbitrary choices, so it makes sense to have this as a move (which the user of a program would have the ability to switch off if they were queasy about using AC). It so happens that for this problem choice is not needed, since one can simply take all possible pairs $(U(y),V(y))$ instead of choosing just one for each $y$. Nevertheless, Skolemization seems like a good move to have.
    
The second move type that is useful but that we do not have is "de-peeling". If we wish to prove a statement of the form $\forall x\ P(x)$, then we will happily peel the universal quantifier -- that is, we will attempt to prove $P(x)$ for some arbitrary $x$. However, if we have a statement of the form $\exists y\ \forall x\ P(x,y)$ and we make $y$ a metavariable, then the picture changes. We may peel $x$, but it is not enough to establish $P(x,y)$ for a single $x$, even if that $x$ is arbitrary, since we may have made choices that depend on $x$. So we have a situation that is a bit like other situations where we want to prove that some object exists with more than one property, except that here we have infinitely many properties (potentially anyway). What we need to do is simplify the problem but be careful not to commit ourselves too much to one particular $x$. Having simplified, we will with luck end up with a problem $\exists y\ \forall x\ Q(x,y)$, where $Q$ is a simpler statement than $P$, and proceed from there. But for this we sometimes want to bring the $\forall x$ back down into the target, possibly with a view to "de-expanding". As I write this, I realize that de-expanding is something we have not really discussed, though the way expansions are curretly set up, this is not an issue, since they are given as equivalences, without it being explicitly said that one side is defining the other. 
    
The third move type is something we called "naming". We got to a point where a term $y(w)$ (in the notation we were using) had the property that its constituent parts $w$ and the function $y$ only ever occurred as part of the term $y(w)$. It was then useful to give it a name, $q$. The reason was the following. We had a function $y:A\to\Delta$, and $\Delta$ had the important property of being finite. We had a target of the form $\forall w\in A\ P(y(w))$, and wanted the program to get from that to seeing that it was sufficient to prove $\forall q\in\Delta\ P(q)$. One way to do that is to peel so that we have a hypothesis $w\in A$ and a target $P(y(w))$. Then from the hypothesis we deduce $y(w)\in\Delta$. Now this new hypothesis and the target have a matching term $y(w)$. We can decide to call that $q$. That would be the naming step. But there is slightly more to it than that, because we also want to quantify over $q$. So the logical move is to go from $\forall w\ w\in A\implies P(y(w))$ to $\forall q\ (\exists w\in A\ y(w)=q)\implies P(q)$, and then we weaken the hypothesis $\exists w\in A\ y(w)=q$ to $q\in\Delta$. I think the first step there is the move we don't have. 
    
There was also a fourth step that wasn't exactly a move but it was a library result of a rather special form that needed some discussion. At an early point in the proof one has a point in $A$ and another point not in $A$ and one deduces that they are distinct points and therefore that the Hausdorff condition can be applied to them. The library result in question is the very general statement that if $P(x)$ and $\neg P(y)$, then $x\ne y$. (This follows from the principle that if $x=y$, then $P(x)\implies P(y)$, but for several applications it is a more directly applicable form of the principle.) We discussed how a program would spot a match for this principle. It would be quite natural for it to note that it wanted to prove that $x\ne y$ and to consider trying to find a property that distinguishes them. To search for such a property, it needs to look in the hypotheses for statements that involve $x$. It can do that by looking at nodes of the parse tree (in suitable position) labelled with relations, connectives or quantifiers, and checking whether the relevant subtrees contain leaves. MM suggested that once such a match had been found, the relevant statement should be given a name $P(x)$, so that then the match would be easier to identify. Here one also needs a further step to convert $y\notin A$ into $\neg(y\in A)$, but that can be achieved using subtasks. 
    
</details>
    
<details>
    <summary><b>Tuesday 1st November 2022</b></summary>   
    
*Mixed Zoom/in-person meeting with Katie Collins, Timothy Gowers, Bill Hart, Angeliki Koutsoukou-Argyraki, Matei Mandache, Bhavik Mehta and Wills Wynn Thomas*  
    
Some of the topics we discussed were as follows.
    
What is needed for us to make progress on the library? Two things we need to do are to devise a mini-language for inputting library results, and to write a parser for that language that will convert those results into syntax trees that the program can process in a convenient way. We ended up taking the view that the most convenient input language would probably be a kind of pseudo-LaTeX. For example, the definition intersection of two subsets of a set might be written as "set(X) \and subset(A,X) \and subset(B,X) \and x \in (A \cap B) \iff x \in A \and x \in B". (We did not decide on an actual format, so this is just an example of the kind of thing we might go for, and it clearly raises all sorts of questions.) 
    
It was also mentioned that it would be good to describe carefully and implement a few move types that we do not yet have.
   
Should the library be a relational database? 
    
When a result is often applied after a small amount of manipulation, should we add a reformulated result to the library that includes the manipulation, so as to make the result show up more readily in searches? An alternative would be to store the result as relevant if certain conditions are satisfied. In the latter case, the result would be added to the problem state as a hypothesis, at which point the program would think about how to use the new hypothesis (a much easier task than identifying the hypothesis out of all the statements in the library). 
    
There was a technical discussion about use of GitHub -- forks vs branches, when pull requests should be made, etc.
    
How do we represent statements such as that the intersection of two subgroups is a subgroup? In particular, what is a subgroup? If we define it to be a subset that is closed under the group operation, then it is false that a subgroup of a group is a group, since it is just a set. This is, unsurprisingly, a familiar problem to the formalization community, and there are standard ways of dealing with it. We agreed that we would need to address the issue sooner rather than later.
    
What makes one result in the library more basic than another? When one thinks about it, there are different orders at play. For instance, one might wish to say that topological spaces are less structured, and therefore more basic, than metric spaces. On the other hand, typically one teaches metric spaces first, so that one has interesting examples of topological spaces before defining them. More generally, it is very common to develop mathematics by abstracting away from more structured objects to less structured ones. It was suggested that to decide what order we want to take, we should focus on what we want the order to achieve for us. Perhaps the main thing is that we don't want the program to assume an "advanced" result in order to prove a "simple" one. Returning to the example, if we are asked to prove that the inverse image of an open set under a continuous function is open in a metric-space context, then we don't want the program to quote the topological-space definition of continuity. But one way of dealing with that is to make the statement that the open sets in a metric space form a topology and that the two definitions of continuity coincide relatively advanced ones. But it is not yet clear to us what the general principle is here.

Do we want a type system for our mini-language and library? We are still unclear on this point. It may be that we can get away without it. We also discussed the possibility that even if our output isn't formally verified, it might be in a form that an LLM would find easy to convert into a proof in a language such as Lean or Isabelle.    
    
</details>
    
<details>
    <summary><b>Friday 4th November 2022</b></summary>  
    
*Mixed Zoom/in-person meeting with Katie Collins, Timothy Gowers, Bill Hart, Angeliki Koutsoukou-Argyraki, Matei Mandache, and Bhavik Mehta* 
    
We had a long discussion about whether we needed a type system, and if so what it should look like. The discussion included details about how Lean's type system works. An example of the kind of difficulty that comes up is that a subgroup $H$ of a group $G$ can be defined either as a group whose underlying set is a subset of the underlying set of $G$ or as a subset of the underlying set that is closed under the group operation of $G$. Lean has a notion of a set that "comes with" extra data such as a binary operation and an identity. Towards the end of the discussion we considered how we might input the statement that if $G$ and $H$ are groups and $\phi:G\to H$ is a surjective homomorphism, then $G/\ker\phi$ is isomorphic to $H$. By the end, we appeared to be arriving at a position where we would like to be able to input library results in a (somewhat restricted) natural language, and for this to be automatically translated into an elaborated parse tree. For example, one might write, "Let $G$ be a group and let $H$ be a group and let $\phi:G\to H$. Suppose that $\phi$ is a homomorphism and $\phi$ is a surjection. Then $G/\ker\phi$ is isomorphic to $H$." The parser would have quite a lot of work to do here, including unfolding the definition of "$G$ is a group" to the point where it became a quadruple (underlying set, binary operation, identity, and inversion function), and similarly for $H$. As for $G/\ker\phi$, that is more complicated still -- it somehow has to know that it is a group, which isn't a triviality but is more like a library statement, or rather a deduction from the fact that $\ker\phi$ is a normal subgroup. Exactly how this should work is not yet clear.
    
</details>

<details>
    <summary><b>Tuesday 8th November 2022</b></summary> 
    
*Zoom meeting with Katie Collins, Timothy Gowers, Bill Hart, Angeliki Koutsoukou-Argyraki, Matei Mandache, and Bhavik Mehta* 
    
I'm afraid I don't remember much about this meeting. I think it was a fairly chatty and not too technical one.    

</details>    

<details>
    <summary><b>Friday 11th November 2022</b></summary> 
    
*Mixed Zoom/in-person meeting with Katie Collins, Timothy Gowers, Bill Hart, Angeliki Koutsoukou-Argyraki, Matei Mandache, and Bhavik Mehta* 
    
1. We discussed the general question of when it is possible to interchange quantifiers, coming to the conclusion that there is probably not a nice criterion. A situation where it is possible is with statements of the form $\forall y\ \exists x\ P(y)\ \wedge\ Q(x)$ or with statements of the form $\forall y\exists x\ P(y)\ \vee\ Q(x)$. MM presented the following more interesting example: $\forall y\ \exists x\ P(y)\ \vee\ (Q(x)\ \wedge\ R(y))$. To see that the quantifiers can be exchanged, first apply distributivity to get $\forall y\ \exists x\ (P(y)\ \vee\ Q(x))\ \wedge\ (P(y)\ \vee R(y)$. This is easily seen to be equivalent to $\forall y\ (P(y)\ \vee\ \exists x\ Q(x))\ \wedge\ (P(y)\ \vee\ R(y))$. Now use the fact that $\forall$ distributes over $\wedge$ to turn this into $(\forall y\ P(y)\ \vee\ \exists x\ Q(x))\ \wedge\ \forall y\ (P(y)\ \vee\ R(y))$. We can now commute the quantifiers in the first bracket, pull out $\exists x$, and then pull out $\forall y$, ending up with them in the reverse order where $x$ is "chosen uniformly". 
    
TG pointed out that if we quantify over sets of size 2, then the existential and universal quantifiers become $\vee$ and $\wedge$, and the problem of determining whether they can be exchanged becomes a special case of SAT. We didn't show that this case of SAT is strong enough to be NP-complete, but it seems quite likely. So from a practical point of view, it is probably best that we should consider exchanging quantifiers in very easy cases but not try to make it part of the program to determine things like exactly when we can get away with a bulleted variable depending on another one: the order of quantification will usually be thrown up quite naturally by the problem at hand. 

2. We discussed the format for representing library results. We agreed on aliases. (Unfortunately I have forgotten what that means.) 
    
3. We discussed a problem of how the program could "notice finiteness". This is a special case of the problem of "semantic matching" -- noticing that two concepts have closely related meanings -- as opposed to the syntactic matching that we are mainly focusing on. The kind of problem we are worried about is something like this: let $f:\mathbb Z^2\to\mathbb R$ be a function such that $f(x,y)\leq C$ whenever $x^2+y^2\geq M$. Prove that $f$ is bounded above. As humans we would easily spot the proof: the set of $(x,y)\in\mathbb Z^2$ such that $x^2+y^2<M$ is finite, and a function defined on a finite set is bounded, so we can take the maximum of the bound inside the circle with $C$. But how would a program notice that that set is finite? In this case, maybe it would first prove that it is sufficient to prove that $f$ is bounded above inside the circle and then search for library results that might be useful for such a statement. But if we take the 1D version of the problem -- a sequence $(a_n)$ such that $n\geq N\implies a_n\leq C$, then we would typically just _notice_ that the first $N-1$ terms of the sequence form a finite set. 

4. We talked about whether large language models might be useful for handling very easy school-level mathematical facts. 

5. Returning to finiteness, we discussed how a finite subcover should be represented. Many humans would write $\{U_1,\dots,U_n\}$, but that requires the program to "notice the finiteness". It will probably be easier to use a representation such as $\{U_\gamma:\gamma\in\Gamma\}$ together with a hypothesis that $\Gamma$ is finite. (We will also probably in fact go for a function $U:\Gamma\to\tau$, where $\tau$ is the topology, so writing $U(\gamma)$ instead of $U_\gamma$.)
    
</details>    
    
    
</div> 
   
