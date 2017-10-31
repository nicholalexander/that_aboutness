---
layout: post
title: Technical Interviews
date: 2017-10-27
categories: 
authors: nichol
tags: technical interviews ruby ActiveRecord sql dumb
blurb: Yes, I'm the dumbest ruby developer who ever did live.
---

So I had this interview with this guy the other day.  What an asshole.  He wasn't really.  Or was he?  Regardless, what a terrible interview.  I did terrible.  He asked me a dumb white board question, the answer to which was this:

```ruby
1.upto(n) do |x|
  1.upto(n) do |y|
    print x*y
  end
  print "\n"
end
```

Ooooooh, that's so hard!  And that's why I was completely unable to remember any syntax or pretty much anything.  I froze.  Total. Brain. Collapse.  And I was half thinking the whole time, I can't believe I've been asked to nest a for loop.  And then of course I was only thinking about that and then about how I was not thinking about the loop and then... wait, in Ruby... what's a block?  

Jesu.  Then he gives me two tables in a database!  And says how would I find all the users who had a given subscription.

| users | subscriptions  |
|:-----:|:-------------: |
|name|name|
|email|email|

And what I should have said was: I'd write a migration to setup a relation between the tables so I could use ActiveRecord like it's supposed to be (the app was a Rails one so that would sort of makes sense that they would maybe have ActiveRecord) so that I could do `subscription.users` like every other rails developer in the world and why don't you have that set up in the first place?!

What I said instead was "oh um well I don't know the exact sql syntax and you'd have to do a select all from a join or something" and instead sounded like an idiot.  And though I am fully capable of perhaps figuring out the raw sql command it was not at hand to my dumb and spinning brain and instead of telling this guy his two questions were dumb, I left angry and belittled.

I hate pop quizes.  I have never given one in an interview and I never will.  What a dumb way to hire people.  I really really think that.

<iframe src="https://giphy.com/embed/Zv6Apawffpa2k" width="100%" height="284" frameBorder="0" class="giphy-embed measure-wide" allowFullScreen></iframe>