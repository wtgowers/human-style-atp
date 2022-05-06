# Transforming problems using moves 

The following is supposed to represent in tabular form the mathematical statement that the inverse image of an open set by a continuous function is open, or slightly more formally:

For every metric space X, every metric space Y, every function f : X -> Y and every open subset U of Y, f^{-1}(U) is open.

||
|---------|
|X: metric space|
|Y: metric space|
|U: subset of Y|
|f : X -> Y|
| |
| U is open |
| f is continuous |
|  |
| f^{-1}(U) is open |

The first four statements in the list are basically type declarations (though we are not forced to think of them in that way), while the statements "U is open" and "f is continuous" are hypotheses, and "f^{-1}(U) is open" is the statement we want to prove.

This turns out to be a fairly easy statement for a fully automatic prover to prove. It can do so by a sequence of transformations of the problem of a standard kind that closely matches what a human mathematician would do. 

A first step is to expand out the definition of "is open" in the conclusion of the statement. 

||
|-----|
|U is open|
|f is continuous|
||
|(forall x in f^{-1}(U))  (exists delta > 0)   (forall y in X)   d(x,y) < delta => y in f^{-1}(U)| 

