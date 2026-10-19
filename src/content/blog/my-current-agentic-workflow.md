---
title: "My current agentic workflow"
description: "How I work with AI"
date: 2026-03-29
---

Everyone is trying different approaches when it comes to software development with AI. There are people who are using AI autocompletion. There are people trying different shapes of Ralph Wiggum loops. There are people who spend hours polishing a perfect spec before handing it over to AI. Here I'm gonna share how I've been currently working with it. This is by no means the perfect solution, but it is the solution that's working out for me.

I've tried many different approaches, mostly due to the hype. And after experimenting with it all, I've come to realize that there is no silver bullet. You gotta do what works best for you.

Without AI, whenever I was assigned a task the way I would work on it always followed the same patterns (of course this differed according to task size).

1. Try to understand the problem we were trying to solve.
2. Play around with some solution to see if things worked the way I expected.
3. Then after learning from the previous step, I'd probably start having the full picture. And would try to rubber duck with a colleague about my potential solution.
4. With even more context, I'd finally feel confident in designing/developing the final solution.
5. After that, I'd always make sure to do lots of end-to-end integration tests and a bunch of exploratory tests as well, to ensure that whatever I delivered worked and didn't cause potential regressions elsewhere.

Why am I saying all this? Because I think the same should apply to AI. Even if you think you know the entire context of the problem you're trying to solve at first, you probably don't. At least I never did. So, for me, spending lots of time writing a perfect spec never really made the AI one-shot whatever task I gave to it. Mostly because whenever I wrote the spec I didn't have the full picture at all.

That's why I've started working with AI in a way much more similar to the workflow I had before.

1. I give it a brief description of the problem I'm trying to solve.
2. Ask it to do some research and present me with some alternative solutions.
3. Read its output. Ask more questions, ask it to write some test scripts. This usually takes a bunch of turns.
4. By this time, I'm now way more context aware of the solution, so I often clear context and rewrite the original prompt providing my recent learnings and guiding it towards the solution that makes sense to me now and asking it to discuss it with me.
5. Once I'm satisfied with my learnings/experiments, I tell it to write tests to ensure the solution works and doesn't cause any side effects.
6. The tests are important because they become the feedback loop for the agent. A way for them to verify that what they wrote actually works.

I think the main insight at least for me is to feel free to go back to your original prompt and rewrite it. Although you might say with this the agent would lose all its context, I'd argue that even though the agent lost the context, you gained way more. You learned with these iterations. You thought of edge cases and alternative solutions. The chat was your rubber duck.

I understand this way does require lots of back and forth, but I find it helps me understand the problem we're solving way more deeply, which allows me to still be in control of the code generated.