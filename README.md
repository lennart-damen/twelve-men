# 12 Men on an Island

## Introduction
My colleagues and I like to challenge each other with mathematical puzzles. One of the puzzles that took a long time to crack was the '12 Men on an Island riddle' (https://medium.com/starts-with-a-bang/weekend-diversion-the-logic-that-stumped-brooklyn-nine-nine-e3974789ca7e)

The riddle goes as follows:
"There are 12 men on an island. 11 weigh exactly the same amount, but one of them is slightly lighter or heavier. You must figure out which. The island has no escapes, but there is a see-saw. You can only use the see-saw three times."

E.g. you can weigh 3 men against 3 others

 man-man-man              man-man-man
------------------ ^ ------------------

The most intuitive approach is to explore the statespace: if I weigh 3 against 3, the outcomes could be ...
Which is something a computer can do must faster than humans.

At the time, I wanted to learn Object Oriented Programming, and this problem seemed quite suitable for it.

## Concept
You can view the state of a riddle as an object. Each riddle object is defined by:
- U: # of men of which you don't know anything
- L: # of men which could be light
- H: # of men which could be heavy
- N: # of men with normal weight
- tries: remaining # of tries
The initial riddle would be described by the state (U, L, H, N, tries) = (12, 0, 0, 0, 3).

In this state, you can generate the sensible moves that you can do.
In the initial state, you could weight 1-1, 2-2, 3-3, ...

Each of these moves has a couple of possible outcomes. These outcomes are riddle objects themselves.
E.g. the initial riddle in combination with the move 1-1, could yield
- (10, 1, 1, 0, 2) in case the scale tips to one side
- (10, 0, 0, 2, 2) in case the scale balances

By generating children, you can construct a graph of riddles.

## Work in progress
After several different implementations, I figured the best implementation is to view a Move as an object itself.
The graph then consists of Riddle nodes and Move nodes. Riddle and Move nodes have different conditions for being solved.

The only step that needs to be completed is the graph search, which should output when a riddle is solved and when it is unsolvable.
