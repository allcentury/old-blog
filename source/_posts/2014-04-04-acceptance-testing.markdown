---
layout: post
title: "Acceptance Testing"
date: 2014-04-04 16:59:47 -0400
comments: true
categories:
---
Week 7 is a wrap!  I've only aged 7 weeks but I feel like I've learned more in that amount of time than all those years of college.  Programming and web development in general, is simply a snowball ride.  You start with a snowball about the size of a peanut and with enough momentum, well...

{% img http://www.clearpointcreditcounselingsolutions.org/wp-content/uploads/Debt-Snowball-Method-Building-Momentum.jpg %}

So that said, I certainly understand the need to keep going at this pace (unsure how sustainable that is but we'll see).

To bring you up to speed, since my last post we've done a lot!  In the last 2 weeks, we've really gotten into using TDD in rails and it's been a bit hard.  While TDD was more straightforward regarding unit tests, I never even thought about testing my web application with tests.  I thought my fumbling around each page, trying to 'break it', was sufficient enough.

If you're unfamiliar with outside-in development and acceptance tests, the path to follow is generally:

{% img http://coding-is-like-cooking.info/wp-content/uploads/2013/05/london_school_001.jpg %}

An acceptance test is really just a user experience on your site and thanks to some gems like Capybara I'm able to actually move through my web application without going to my web application.  Is there a form on the home page you need to fill out?  Well I can test that, not only that form is there, that it has the right fields and given the right (or wrong) data, it will do something.

Imagine how many ways you try and break those forms, give it a name when it needs a number, a number when it needs an email, and the list goes on & on.   Thankfully if I just write some automated tests once, I can reuse those time and time again making my application even more failsafe.

I'm excited to finish the next 3 weeks strong but I'm hopeful I land at a place that will continue to let me grow at this pace!


