---
layout: post
title: "Day 2 as a Launcher"
date: 2014-02-18 18:50:10 -0500
comments: true
categories:
---

These hour long train rides from Launch Academy's "Mission Control" are nice for a few things - 1.) I actually get some time to decompress from long hours of staring at manuals and online docs and 2.) I get to actually listen to some music.  Anyone who knows me knows I love music and would be completely content with just closing my eyes and listening for hours.

However, the nicest part about the train (besides the free-wifi - thanks MBTA) is that I actually get to review the madness that happened during the course of a day.  When you're "in" the moment, it's hard to step back and reflect on what you just learned.

Today in class we went over flow control in ruby and loops.  These topics aren't foreign to me as I explored them heavily many years ago in C & C++.  The ruby naming conventions and block requirements are a bit different from the languages I already mentioned but I found that interesting.

See in other languages like C, you'd have to explicitly define each variable and it's state, but in Ruby you can do this:

``` ruby Blocks

array.each do |x|
  puts x
end

```

Where did I define "x" there?  I didn't.  The each method is so perfect that it doesn't even care that I didn't set the state of "x".  While I had been using the each method and a while loop almost interchangeably since the fall, it wasn't until that I realized I can do so much more with less!  In fact, Dan Pickett - head of LA told us that Ruby's each method is really a fancy while loop but that I should let the language inherently simplify my code.  Brilliant!
