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
This is a public record of what is discussed in our face-to-face meetings, partly to remind ourselves of avenues that we started exploring but temporarily abandoned, but more importantly as a way of being more inclusive to people who are participating remotely.

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
 
 </div> 
