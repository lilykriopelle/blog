---
layout: post
title:  "Teaching Debugging"
date:   2015-12-02 10:47:53 -0500
categories: teaching
---

At [App Academy][app-academy], we emphasize early and often that a large part of an engineer's work is debugging (after all, nobody writes perfect code all the time). Therefore, it is crucial for aspiring engineers to become efficient debuggers. I would argue that skillful debugging is the most important ability for a programming student to develop.

There are lots of things one can do to become better at detecting and squashing bugs: learn to read error messages, become familiar with common errors and their causes, learn to write and run tests, become proficient with a well-supported debugger for the language you're working in, learn to read documentation and source code for libraries your code interacts with, and the list goes on. But the hardest thing to teach isn't so much a skill - it's an attitude.

Often, a student will ask for help with a problem, and their question will take the form "I know `method_a` works, but `method_b` is broken and I can't figure out why". Thinking this way is tempting - if you've written `method_a` yourself, and tested it with a couple of reasonable inputs, you might not have any reason to believe that it could be the source of the problem. And under any kind of time pressure, we all focus in on the areas we believe could be causing the problem. But usually, this kind of thinking creates a blind spot that might obscure the actual issue and lead to wasted time.

When I come to a student's code to help them debug, I don't have any assumptions about which parts work and which do not. Free from such assumptions, the logical approach is the only one I can take.  I start at the "scene of the crime" (where something went wrong), and work up the call stack until the offending code is detected.  

When I am met with resistance ("But I already tested this part, I know it works!"), I explain that because I don't know their code (after all, I didn't write it), I have to walk through it step by step. I make sure to reiterate that slowing down and stepping through code line by line is not a sign of weakness, but of thoroughness. Frequently, we find that the error is coming from part of the program that the student was most confident about.

Teaching programming has made me a much better debugger. The more I model debugging for my students, the more quickly and easily I am able to disregard assumptions about my own code. In fact, I now look forward to debugging sessions as an opportunity to learn more about myself and my own mind by reflecting on the assumptions I made and why they seemed reasonable at the time I made them. I encourage my students (and all programming students, really), to think about debugging this way - not as a chore, but as an opportunity.

[app-academy]: http://appacademy.io
