---
layout: post
title: "AR = Launcher * .5"
date: 2014-03-21 17:56:51 -0400
comments: true
categories:
---
I am now half launcher, half I have no idea what I'm doing.  It feels good - mostly.  The last few weeks have been especially rewarding because projects are starting to take shape.

We've spent the last week really focused on ActiveRecord and my explicit nature has cursed the Object Association Gods.  It's a little too easy, isn't it?

In SQL I have to do:

``` sql movie_search

SELECT *
  FROM movies
    ORDER BY rating DESC;

```

in ActiveRecord the statement is simply:
``` ruby movie_search
Movie.order(rating: :desc)
```

The relationships though are really where ActiveRecord starts to do some magic.  In SQL you have to join tables together like

``` sql movie_studio
SELECT movies.title, studios.name
  FROM movies
    JOIN studios
      ON movies.studio_id = studios.id
        WHERE studio.id = 2;
```

However in ActiveRecord:
``` ruby movie_studio
Movie.find(2).studio
```
Well.  Can't really argue with that, can you?

All in all, the last 5 weeks have been awesome!  I've been tinkering with rails for a bit now and while tutorials are great, I've felt like I've really dived under the hood at Launch Academy and it's infinitely increased my learning power & potential.  Ending today on a high!

