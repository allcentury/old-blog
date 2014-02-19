---
layout: post
title: "Up Up and ... Crash!"
date: 2014-02-19 18:18:21 -0500
comments: true
categories:
---

Yesterday was a long one but thanks to my girlfriend & my mom, I was able to get a good nights rest.  I woke up a bit tired today but towards the end of the day I felt great.  Class sessions are going well, some problems seem easy while others are taking me a bit more time.  Why did writing a multiplications table take me 3 separate tries and an hour?  Sometimes I think half the battle of programming is simplifying the problem before coding.  I was trying multidimensional arrays with complex iterators to try and format the output to match the test case.

Then a fellow student came by and said he was struggling too - after a few moments talking to each other, we got this:

``` ruby Multiplications_Table
def multiplication_table(size=12)
  x = 1
  y = 1
  while x <= size
    print "#{x*y}"
    y +=1
    if y <= size
      print "\t"
    end
    if y > size
      puts
      x += 1
      y = 1
    end
  end
end
```
Well duh.  Our lead mentor (Adam) encouraged us to solve a problem known a few years back in the hiring world, a little test called FizzBuzz.  The solution is all over the internet so I won't post it, but shame on you if you're reading this looking for the answer!  I can't speak as to why other developers can't solve this problem but I'm glad we talked about it in class.
