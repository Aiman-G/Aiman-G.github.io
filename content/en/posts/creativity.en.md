---
title: "Creativity Is Systematic Hallucination"
date: 2026-03-16
description: "A personal reflection on creativity."
categories: ["tech"]
draft: false
tags: ["LLM", "AI", "Creativity"]

---

What is creativity? In my view, it is simply the ability to create something new, whether in art, handicrafts, food, or any other domain.

But has any human ever created something from nothing?

I mean something truly new that is not, in some way, a combination of things that already exist. I would say no.

Any new theory, idea, or product is often a combination of two or more older ideas. If you reduce anything new to its most basic building blocks, those blocks are usually old.

In this sense, creativity is the ability to connect things systematically.

This systematic connection and exploration are what distinguish creativity from hallucination.

Creativity can be seen as a kind of systematic hallucination, while hallucination is simply random connection or recombination.

Here, on this page, I use **hallucination** to mean jumping between ideas that seem unrelated to someone who is not sharing the subjective experience , the listener. I do not know about the other side; I guess no one hallucinates while knowing that they are hallucinating.

Will AI be creative?

Yes. If you have the resources: data, compute, and the ability to search and connect, you can create “new” things.

Isn’t AlphaFold creative? I would say it is. The output of AlphaFold is, in a sense, genuinely creative: it produces new and useful results by exploring patterns beyond ordinary human intuition.

But in human society, censorship and restrictions on the wandering mind can limit creativity. The same applies to AI.

If hallucination is completely forbidden, then AI becomes, as people say, just our collective “online” brain.

A wandering mind is a fertile ground for creative output, as long as it can occasionally direct that wandering toward an objective.

The same is true for an AI wanderer.

One way to build a creative AI may be to induce in it some form of controlled wandering (guided wandering) , unless, of course, we are building a specialist system that wanders only within a restricted space, as in the case of AlphaFold.

An AI system with access to the knowledge of the internet, combined with this kind of controlled wandering, may occasionally come up with genuinely new ideas.

But what is the cost of induced wandering?

If inference in an LLM is already such an expensive task, and the model is still, in some sense, just a sequence generator with induced RL, then a true general wanderer would likely be even more expensive.

Creativity is expensive, unless you are focused,  your brain wanders in a small defnied space. 
This cost comes from the fact that creativity is of combination. 
If you have 10 ideas to combine(foreget the cost evaluting ideas after combining them), so let us stick to the cost of combination only. 

the cost of combination is wandering(searching), 

if you have \(n\) ideas, and creativity means combining **2 or more** of them, then the number of possible combinations is:


This can be simplified to:

\[
2^n - n - 1
\]

\(2^n\) is the total number of all possible subsets of \(n\) ideas.



For example, if you have \(10\) ideas:

\[
2^{10} - 10 - 1 = 1024 - 11 = 1013
\]

So even with only 10 ideas, there are already **1013** possible combinations.

If you have \(20\) ideas:

\[
2^{20} - 20 - 1 = 1{,}048{,}555
\]

So with 20 ideas, the number of possible combinations already exceeds **one million**.





Except, it is not that simple. 




The mind does not wander only among a predefined set of ideas. While exploring the ideas you already have, new ideas appear in between.

Assume you are miserable. Every day, you eat lunch at the supermarket beside your workplace. The ready-made meals are boring, so you decide to make your own simple meal from whatever is available there.

Instead of buying a tuna sandwich, you buy bread, cheese, and honey. You make a honey-and-cheese sandwich.

The next day, you wander again through the same space. On one shelf, you see sesame halwa. Now a new element enters the game. You remove the honey and replace it with halwa(BTW, try it ,  it is a very common breakfast in Yemen.)

Then, out of nowhere, someone appears near the supermarket selling boiled eggs. Now yet another idea enters the search space. You start thinking: maybe eggs, cheese, and honey[^1] could work together.



You begin with a limited set of ingredients, but while searching among them, new ingredients appear. The space itself expands while you are exploring it.

So the real cost of creativity is not only the number of combinations inside a fixed space. It is also the cost of dealing with a search space that keeps changing while you search( **we have not spoken about the evaluation cost so far, and we  will never do**)

It is not merely a search problem; it is a dynamic search in a dynamic space.

so , a focused mind is less costly because it wanders within a smaller space. A specialized AI is cheaper for the same reason. The more bounded the space, the more manageable the combinatorial explosion becomes. But this is only true if we already know that novelty can emerge from combinations within that predefined space. It also depends on treating ideas as discrete units. If the search space is continuous, then the number of possible combinations becomes infinite.  



This, makes us think differently about creative people.

How do their minds work? How do they explore ideas? Is creativity extreme luck? Or is it the repeated return to the same set of ideas until a useful new combination appears?

Perhaps truly creative people develop a kind of selective power ( a taste) that reduces the search space without killing the wandering.

 





[^1]: Combining honey with boiled eggs is, in my subjective experience, a food hallucination.

