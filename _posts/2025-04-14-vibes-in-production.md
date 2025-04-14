---
layout: post
title: Production Vibes
date: 2025-04-14
categories:
authors:
- nichol
tags: ai vibe coding production iteration experienced engineering
blurb: There's a spectrum between Vibes and Craft.
---

"Vibe coding" as a phrase is sort of driving me crazy.  So in order to determine if I was being HYPEnotized, I decided to sit down and build a small app for my daughter - a little react doohickey of a thing to help her in her college search.  Along the way I had my breath taken away by the amazing experience of working with agents and also started to think about the spectrum between pure vibes and what I consider to be production level code.

## Vibing

Using mostly Claude agents, I tried to get into the vibe.  Setting it up was easy, getting it going was easy, and the results were shockingly amazing.  Having been lovingly embracing AI and ChatGPT into my work flow, this was an obvious function step and I sort of loved it.  I embraced the idea of not looking at the code and just accepting everything - the only thing that mattered was what it looked like and what it did.  You know, like Kai Lentit, professional Vibe Coder @ X says:
<a href="https://www.youtube.com/watch?v=JeNS1ZNHQs8" target="_blank">"Vibes only."</a>

And lo - maybe 45 minutes later I had a react app built and deployed that was backed by a json data set that had been converted and suplemented by vibes and additional scripts to scrape websites that allowed for searching, sorting, adding, mapping, filtering, a visual sticky note interface, and most importantly, emoji annotation!  No joke it was wild.  I think its the most breathless I have been experiencing a new technology.

## The Horrors

Having thoroughly been amazed I decided to dig into what I had actually created.  It was astonishingly bad.  Some of what we wound up with was:

* hardcoded GPS coordinates in the map component instead of in the json data.
* the filter had been duplicated and implemented differently on each page that it appeared on, instead of reusing a filter component
* all of my edits and changes had created unusued code, confused and incorrect comments

Obviously this also had no tests, no style guide, and I wasn't a huge fan of how the structure of the whole project had evolved.

![scream.jpg]({{ "/assets/vibes_to_production/scream.jpg" | absolute_url }})

Having seen it before, I realized that what I was looking at was the equivalent of having created a waterfall design doc, split it up and provided parts to a distributed team with no communication and no collaboration, and then stitched everything together in the end.  It works, but we know this is not how we build software.

## Spending the Credits

None of this, however is to dimminish the miraculousness of the whole process.  And most importantly, nothing about our situation, except the expenditure of credits, prevents us from moving this code base towards production.  Sort of as a lark, I decided to see what I could do to clean up this code, at least at the margins.

How about some Vibe Tests?  Unit tests were really easy to set up and get going, though this was the first place the agent stumbled with React Testing Library.  The AI was not importing correctly from RTL and so threw my vibes off.  I had to touch the keyboard!  But a quick fix and it was back to chugging along.  After that, however, I noticed that everytime it wrote a test that failed, it relied on mocks to getting the test to pass - which in this case resulted in overmocked tests without any actual exercise of the underlying code.  A little bit of babysitting and oversight caught (most?) of the situation and got us some actually working tests.

I decided to throw in a couple of system tests to increase my overall trust and two prompts later had Playwright, a smoke test, and a decent feature test up and running.

With some tests in place I spun them up in `--watch` and decided to refactor these hard coded GPS coordinates and this filter mess.  Having tests running, on top of the agent input and feedback, felt a little otherworldly.  I loved it and I was able to make some pretty quick clean ups.

Lastly, I decided to get some style guide formatting going.  Claude was very accomodating by installing the Airbnb style guide in seconds and then promptly disabling every rule that caused a failure!  Again, as with the tests, some babysitting was required.  Prompts similar to: "No, fix the actual violation" were in some cases helpful and in most cases not.  The style fixes were the ones that seemed to require the most hands on work, which was sort of suprising to me.

## The end result

Looking back at it I was feeling pretty good.  But I realized I still didn't have a piece of "production" code that I would be happy to let a colleague or mentor review.  It was less blatently horrible, it had some hints of good practices, but it was still a bit of a frankenstein piece of code.  Yes, sure, an MVP in an insanely little amount of time.  And with a test harness and some basic attempts at sanity.  But still stitched together.

Maybe it's useful to start thinking about how vibe coding fits on some spectrum of software development?

Here's an idea I was kicking around:

![Vibes to Production Spectrum]({{ "/assets/vibes_to_production/spectrum.svg" | absolute_url }})

We know the code we write, if it works and gets traction, will become defacto production code.  My suspicious is that there is some value in spending some of your credits to move your vibe a little bit towards the right in order to get you closer to that golden balance between moving fast and getting something up and having something that you and your team are going to have to live with for a long time and therefore needs to be maintainable, structured, and reliable.
