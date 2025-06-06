---
layout: post
title: A crack in the foundation
date: 2024-12-29
tags: ["system design", "kubernetes", "linux", "operating systems"] 
---

Even though I did take a break from hobby-coding (i.e. pushing things to any of
my GitHub repos) in the last three weeks, I was far from inactive in my computer
science learning paths. I just didn't update this blog, I suppose! I have
learned that there are a couple of big gaps in my computer science foundational
knowledge--acceptable for when I joined the field many years ago, but starting
to show now.

Those are:

* Databases and system design
* Operating systems, both specifics for Linux and general concepts
* Kubernetes

Then things I also have gaps, but didn't even start studying yet:

* Computer networking
* Security

## Databases and system design

I seldomly have to do proper database design as part of my job. I was very
mindful of data migrations at some point in my career (because I had to do a
couple of them at some point), but it wasn't a difficult one. Data was well
behaved with no concurrency problems, since all of the data points would come
from deterministic batch pipelines that would not override each other.

I have found a couple of good resources for that, mostly in the form of system
design lectures:

* https://www.youtube.com/watch?v=3loACSxowRU&list=PLhgw50vUymycJPN6ZbGTpVKAJ0cL4OEH3

This series is good, but it's not my type, I suppose. He instinctively does all
the right things you should be doing for good design: requirements (functional
and non-functional), then architecture overview, then zoom into the core
components. I, however, missed a trade offs discussion (which I assume he didn't
add because of time limitations).

Let me explain a bit further: in the induction for traffic-team at Google, we
have a ritual which is "give a 101 presentation about the stack", as part of
joining oncall. Most people understand the pieces, and go over the "life of a
request path". This guy does that, so in that sense it's good. I remember,
though, watching one of our more experienced SREs giving that presentation. It
went like this:

"Let's suppose that you have a server that has a website and you need to serve
that. Now what?"

From there, he carefully went from a single server to Google's very elaborate
production network high-level components, not only saying what does components
do, but also highlighting what each component was trying to solve when it's
first introduced. It was a long presentation, but it was well worth our time.
I have tried to do something very similar when I was practising the design of
a tiny URL service (
https://github.com/royalsflush/system_design/blob/main/tiny_url/tiny_url.md). I
have to caveat that this was just on the reliability requirements (i.e. how
many nines of availability we wanted to have).

I think that would be a cool idea for a series about system design, as a whole:
vary on query types, vary on reliability requirements, vary on latency
requirements and see the system change.

* https://github.com/donnemartin/system-design-primer

System design primer is a great resource. The researching is excellent, and I
quite like the explanations. I have consulted it many times, as well as its
reference materials. The biggest problem with it is structure. The pieces are
all there, but it requires you to self-assemble them, and to have the
fundamentals to do so (a thing that this blog is particularly concerned about!)

That said, for an unstructured free resource, it's a great time. I went back and
forth a lot between this one and the resource above to get a deeper
understanding. I'd start with a system design problem, then I'd compare my
solution with both of them. I would find that they also focused on different
things, and the multiple perspectives was extremely valuable.

* [Designing Data-Intensive Applications (Martin Kleppmann)](https://www.amazon.co.uk/Designing-Data-Intensive-Applications-Reliable-Maintainable/dp/B08VKMNDBN/ref=sr_1_1?crid=3PE8P6PKXQ8LS&dib=eyJ2IjoiMSJ9.waCcWuQztpEOeoLAQmtfulK_RjQENSrSgLVAPHpdcwv4hLKM-QJkeWE2sMrn1Bhb.zJRl7kqUKnEzEG9aa2gsfN0jVoHOaGhoVHWJNwt31hk&dib_tag=se&keywords=designing+data-intensive+applications+by+martin+kleppmann&nsdOptOutParam=true&qid=1735483692&sprefix=martin+klep%2Caps%2C94&sr=8-1): 

The real MVP of this part was "Designing Data-Intensive Applications". This
book sits at almost 22 hours for the audio book and it is extremely
comprehensive. It covers an incredible range of topics related to data, and I
cannot recommend it enough. Most importantly, it doesn't cover only "this is
used for that", but also "this is the problem that we were trying to solve when
we invented that solution". There's this part on characterising transactions
that goes on a ladder of asynchronous/fast to synchronous/slow that he presents
a solution, then he presents the drawbacks of that solution, with an alternative
that has other drawbacks, but solves the previously stated problem. It's a
phenomenal read.

However, keep in mind that, while the book has plenty of examples, it's not
going to do the assembly of the pieces for you. If you read this book and
someone tells you to design Twitter or Youtube, you're not going to be able to
do it, necessarily. You'll have all the information to do it, but the other
resources in this section are better suited for integration.

## Operating systems

This was the part that sounded the alarm for me. My knowledge of operating
systems is not good. I have some ideas, but they're all very jumbled in my head.
This vague familiarity with most topics, but no solid understanding of the
concepts and how they link to each other. No good, I feel like I'm bullshitting
people when I have to talk about the lower levels of the stack.

In this part, the difference between computer science and IT became abundantly
clear to me (at least how the industry classify those two things). There are
two types of courses in this section: the ones that are very "technology
focused" (i.e. learn how to Linux/Windows/UNIX, etc, which is classified as IT)
and "learn the principles that govern this area" (broadly computer science). Let
me be clear: I'm not for snubbing one for another--I think that any professional
needs both to keep up with the world. You need specifics in order to get your
day-to-day tasks done, and you need concepts and context to evolve your
understanding and keep up as things move around you.

In that sense, I was interested in both, but as a personal preference, I prefer
to go concepts first, then specifics. I didn't know that preference before
starting these studies, though! Here are my sources:

* [Introduction to Linux (LFS101)](
https://trainingportal.linuxfoundation.org/courses/introduction-to-linux-lfs101)

A bit of an obvious start, I suppose, but I figured the Linux Foundation was
likely the best resource to get my hands dirty on the foundation of Operating
systems. I was... mostly wrong. It's about Linux, but not in a way that I wanted
it to be. It goes over, for instance, distros, common applications, GUIs, the
history of Linux, etc. There are really interesting pieces there, and I think 
the practical knowledge is very useful.

However, as I mentioned above, I was keen to understand a bit more of operating
systems from a conceptual standpoint. I didn't know it back, but it has become
increasingly clear to me as I went through this course.

* [Linux for Beginners (Jason Cannon)](https://www.amazon.co.uk/Linux-Beginners-Introduction-Operating-Command/dp/B00LF9XNUO/ref=sr_1_1?crid=1GUOXZII2E3G1&dib=eyJ2IjoiMSJ9.Q4eqGCPPMlp9-3gjvt-sdeZnmAJX2mDbukykxAk6Q6pL-5-zLAvdWbQ6FCFogLSgd9YxAPWh5q4NbpbvGSU71PxZvev5yXPGaJEl1HV3lNWJjOwEWgJVksuuwtt5MyEp75LuHtsNQoYO2AuEa38w4kDzj09jHAkh7YTCU2IY5am77b2EeaW7HT5iCEf-o07FpjETZhWH5sZ6EvXgqcgLU1lGocc0ifn9NtuMeqTYPpc.RBDo23_SyrurSG9k1f46kNlBb_OW9_3WHnfx8WIu1ro&dib_tag=se&keywords=linux+for+beginners+jason+cannon&nsdOptOutParam=true&qid=1735482373&sprefix=linux+for+beginners+jason%2Caps%2C81&sr=8-1)

This has the same drawbacks of the other courses. It's a book about how to do
things in Linux, so it's going to tell you how to install and use Linux. It's
more distilled than the LFS101, so more beginner friendly.

This book served well as a repetition of content that I have seen elsewhere. It
also does something that I really like: it covers "useful patterns for
particular commands". I cannot stress how nice that is, given most Linux
commands have 30+ options each.

* [The Linux Basic Course by tutorialLinux](
https://www.youtube.com/watch?v=bju_FdCo42w&list=PLtK75qxsQaMLZSo7KL-PmiRarU7hrpnwK)

I loved this course. I'm serious, I even added David Cohen to my Patreon, I
think he's phenomenal. There are many reasons I like this course, even though
I tend to be more theoretical, and David is clearly more practical. It's super
comprehensive, for one, it's 80 videos long of a solid ten minutes each. Every
video concerns itself with a topic with examples.

Now David does something really clever: he varies the level of abstraction we're
dealing with through the videos. He's dealing with processes and telling us how
to navigate processes, then he stays "this is the abstraction that you need to
know here" (in this case, that Linux treats everything as a file. Martin
Kleppmann has made a similar argument in his book, that one on the backbones of
Linux design is the idea that all programmes receive as an input and output a
file descriptor, and how that idea gives way to being able to pipeline different
programmes together. David makes a version of that statement which is less
theoretical early on, while giving us enormous amounts of practical information.
This mix of depth of knowledge with things you can immediately use is perfect
to get someone with the right starting points.

The other big benefit is that David is both knowledgeable and charismatic. That
makes his videos a really easy watch. Highly recommended.

* [Operating Systems by Neso Academy](
https://www.youtube.com/watch?v=vBURTt97EkA&list=PLBlnK6fEyqRiVhbXDGLXDk_OQAeuVcp2O)

This is way more what I was looking for, it's a lot more conceptual. It goes
over my favourite things about topics ("why do we need operating systems in the
first place", the first question you should ask yourself about it!), then he
distills each piece of an operating system.

On the downside, the narrator has a quirk that I couldn't quite tolerate. He
says every single sentence twice. Not a paraphrased version. The exact same
sentence. After a while, this habit started getting to me, despite some solid
content. I feel very pet-peeve-y...

## Kubernetes

This relatively specific on Kubernetes the technology is because I'm starting
to work on Kubernetes (both as an apps developer and as a contributor!). So I
need to understand what's going on. Again, my Kubernetes knowledge is sparse and
I don't feel particularly confident in it. But it's my first dabble, so
hopefully I'll get somewhere! Here's what I'm doing for my Kubernetes parts:

* [The Kubernetes Book (Nigel Poulton)](https://www.amazon.co.uk/Kubernetes-Book-Nigel-Poulton/dp/1916585000/ref=sr_1_1?crid=1QCAO67FWM9DQ&dib=eyJ2IjoiMSJ9.eoh-F6MY903bxHfXnFi4u-QfT5JP9RlvjYmLq-u_oOalfqO_SsB7vj2QDWzjUto_4-Y_T-UhxcHOIigw7WH4aee8NJoHgm1OqlqgfJ7wlX2d9laVLpyg9F-_yzMcxCNMHcXy1ag_JQ4a9f3aGMnH697DYd9OMQ8nSOoM1w3CdKxWumYpPinbOSDbh5hNYSBD1EKEmkFkpNd5Zf8YFm3QzYY_zYkAz4Bp29lh55EjA6s.cU3cU_CiKHB3aYx_iVUcK2MnB0aAjoj_1CaB3vmB-dg&dib_tag=se&keywords=kubernetes+book&nsdOptOutParam=true&qid=1735485600&sprefix=kubernetes+book%2Caps%2C84&sr=8-1)

I'm still at the start of this book, but so far, it has been a worthwhile read.
It's a good blend of practical and theoretical (and the author, to his immense
credit, makes a deliberate decision to cover it like that). I also like the
historical knowledge--the evolution of Kubernetes' approach to its container
runtime engine is quite interesting. But, again, I'm relatively fresh on this
one

* [KubeLearn iOS app](https://apps.apple.com/gb/app/kubelearn/id6502287440)

I have downloaded that specifically for the tube :) I'm normally standing and
normally can't listen to audiobooks. There are a couple of short lessons on
the usage of Kubernetes. They're bite sized and cover very specific aspects (
for instance, the most recent one I did involved annotating an upgrade with a
change log)

I currently don't have the foundational knowledge to benefit from this app as
well as I would like. The exercises are quite specific and I feel like I need to
go to the kiddie pool before I play here.

## Gap paranoia (CompTIA foundational certifications)

Since I found out that I have so many gaps in so many places in my computer 
science foundations, I have decided to look at broad courses and see where my
levels are at for each general area that people cover.

* [CompTIA IT Fundamentals](https://www.codecademy.com/ext-paths/fc0-u61-comptia-it-fundamentals)

This is quite extreme in the levels of paranoia, but it was an interesting
exercise. I have been doing, for the past week, the prep for ITF+, which is a
pre-career IT certificate. It has been super interesting. Some parts I knew
quite well, some I was like "hold on a minute, what's happening here". I want to
finish this course to get a proper assessment of where my weaknesses are.

## Conclusion

I'm fascinated with going back to study. I'm learning so much. And it's funny,
because some of the things are immediately applicable to my job, even when I
didn't expect them to be. My comments in design documents are more well
reasoned, the things I focus are different, and just the amount of confidence I
generally have has shifted immensely.

I'm aware, though, that a lot of the studying I'm doing here is very
theoretical, very book-driven. That's a bias that I'm aware, and for now, I'm
not trying to fix it too hard. It's clear to me I had the opposite bias for many
years. I'm noticing, though, that with the conceptual knowledge, the practical
knowledge sticks much better too. So I think it's worthwhile to me to continue
on this path for a bit

Finally, here are a couple of meta things I learned:

* When learning you have the choice to navigate through your different levels
of abstractions, or go through different angles/slices of the same problem.
Deeper learning happens when you have access to different slices of the same
thing in your head. For a computer science topic, I can imagine you having a
"design overview slice", a "design evolution slice", a "products requirements"
(and its historical equivalent) slice, etc.

* It's important to know what you're looking for, in terms of content: do you
want knowledge to perform a particular task, are you looking to deepen your
expertise in a particular area, are you trying to make connections through
different areas? All those goals have merit and require different focus.
However, like me when I started my journey on this, I didn't quite know what I
wanted, so it's worth keeping in mind that goal refinement can and should be an
iterative process

* Recapping all of this in a blog was a super useful exercise to solidify my own
meta understanding about the topics

That's it for now!
