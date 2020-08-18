---
layout: post
title: Dealing with technical debt
date: 2020-03-05
tag: 2020,management,programming,team
description: Technical debt is just a fancy way of saying that something will bite you in the ass in the long term.
author: Marco Monteiro
categories: [2020,management,programming,team]
---

Technical debt is just a fancy way of saying that something will bite you in the ass in the long term. However, in every project this is something very real that every Lead Developer has to deal with almost in a daily basis.

Here I'll try to describe on how to avoid it it, or at least identify it as soon as possible so you can plan ahead.

<!--more-->

First of all, if we're talking about technical debt, there's something that you can be sure, you'll have to pay it in the future, in one way or another. However I'm not here to say that this is something that should be avoided at all costs. It's not! There's some really good reasons  to accept some form of technical debt. Maybe there's a deadline, or the dreadfull marketing team made some promisses that you'll have to deal with. Or worst of all, management just made some crazy demands that you have to follow. These are just some examples. There's many more, but I think these everyone can relate to.

With this in mind you should always accept some form of technical debt with a deadline in mind, but if you do so, make sure you have a backup plan to fix it in the future. This is how you balance business and your codebase. Never ever, accept technical debt without a backup plan on how to solve it in the future.

I'm going to quote Martin Fowler here:

> If you have this kind of exponential relationship, then if you do it more frequently, you can drastically reduce the pain. And this is what happens with Continuous Integration - by integrating every day, the pain of integration almost vanishes. It did hurt, so you did it more often, and now it no longer hurts. - In [Frequency Reduces Difficulty](https://martinfowler.com/bliki/FrequencyReducesDifficulty.html)

<center>
![graph](https://martinfowler.com/bliki/images/frequency-reduces-difficulty/graph.png)
</center>

What I mean is, managing technical debt is something that you'll learn to do once you start acknowledge is that this is something that you do often. What normally tends to happen is that us, Lead Developers are quite good at identifying these technical debts, however we tend to slack on solve them. Sure this might be ok on smaller projects, where you just have to be sure to avoid them on the next project. But what about big projects? That is just something that you can't avoid, that will probably mean that somewhere in the future you'll have a very dificult conversation with management saying that your app needs a complet re-write. I know! I've been there and it's not pleasent.

How to better understand your codebase so you can identify your technical debt easly?

First you need to check your version control often. Try and see how your developers interact with your code. See what part of your code is being used most of the time. With this you can identify these key areas:

* > **Hotspots** = where most developers are working
* > **Refactoring targets** = prioritize change
* > **Change coupling** = implicit change in patters
* > **Code biomarkers** = aim to indicate specific properties at very low code base

Then you should ask yourself the following questions:

* > Where should we focus improvements?
* > Where are the risk areas?
* > Is team productivity a problem?

When you answer those questions, then there's time for the walk of shame and start paying your debt.

<center><iframe src="https://giphy.com/embed/vX9WcCiWwUF7G" width="100%" height="270" frameBorder="0" class="giphy-embed" allowFullScreen></iframe></center>

But how?

You have many options here and you should pick the one that aplies to your case.

You can allocate more time into the development of said feature and that might solve it because this were rushed. This can be done by making a that a team priority and thats what everyone will be doing until things are solved.

Another way of paying it is actually making a rulle of having a technical debt day per week or month, were you pick days where everyone in the team will do it.

You can just choose to educate your team about it, this can be an option with just small debts in small projects, otherwise education can only go so far.

Should definetly have a talk with management and marketing about it so in the future deadlines wont afect the project as much.

There's only one thing that you might be tempted to do, but maybe it's not really an answer. Hire more developers. This seems like a great idea at first, but sometimes you want to solve these issues with your team before bringing more people into the mix.


