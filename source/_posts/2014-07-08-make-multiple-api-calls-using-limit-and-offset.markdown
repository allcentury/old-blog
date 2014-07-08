---
layout: post
title: "Make Multiple API Calls using Limit &amp; Offset"
date: 2014-07-08 14:59:53 -0400
comments: true
categories: 
---
Earlier today I needed to get some data from the Yelp API but I didn't need
anything more than a list of businesses within a particular state.  I did an
initial search on Yelp's site and saw there were over 300 businesses that met
my search criteria so I decided to write a quick program to get all of the
information I needed.  

If you're reading this you're probably aware that Yelp (like many API's) has a
limit of the search results, in thise case it's 20 (this is as of v2 of their
API).  I've made my code easy to change so by all means replace any of my
variables with your own criteria.  I'm going to put up a gist of all of the code though.

First things first, you need to register your app with Yelp <a
href="http://www.yelp.com/developers/getting_started">here</a>.  From there you
need to copy the 4 codes they give you into this:

```ruby yelp-api.rb
require 'rubygems'
require 'csv'
require 'json'
require 'pry'
require 'oauth'

consumer_key = ''
consumer_secret = ''
token = ''
token_secret = ''

api_host = 'api.yelp.com'

consumer = OAuth::Consumer.new(consumer_key, consumer_secret, {:site => "http://#{api_host}"})
access_token = OAuth::AccessToken.new(consumer, token, token_secret)
```
I've left my gem list as-is and we'll touch on most of these but I suspect you already know what they do.

Ok, so the first goal is make an API call to make sure we get something that we suspect.  Let's add this to our code:

```ruby yelp-api.rb

search_term = "flowers%20candy"
location = "massachusetts"

path = "/v2/search?term=#{search_term}&location=#{location}"
response = JSON.parse(access_token.get(path).body)
puts response["businesses"]
```

So we're searching "flowers candy" with a location of Massachusetts.  This is
not only a tutorial on API calls but also a friendly reminder to buy your SO
some flowers and/or candy.  You can thank me later.  

You should get a response like this:
<img src="http://i.imgur.com/OscOauk.png">

So that response has all the data we want and yelp is kind enough to tell us that 316 businesses meet that search criteria.  That's great and all but they only give us the first 20 what if we want all of them?  We could do a loop 16 times (318 total / 20 per fetch) but how do we change our API call to get the next 20 and the next 20 and so on.  Thankfully almost all API's that have JSON response will give you a way to paginate or limit/offset.  Here Yelp wants us to use limit/offset and you do that by adding that to your API calls like so:

```ruby yelp-api.rb
resp = []
offset = 0
limit = 20 
while !(response["businesses"].empty?)
  path = "/v2/search?term=#{search_term}&location=#{location}&limit=#{limit}&offset=#{offset}"
  response = JSON.parse(access_token.get(path).body)
  resp << response
  offset += limit 
  sleep(1)
end
```
Well this code should be somewhat straightforward but I'll go through the
important parts.  We start with an offset of 0 that's because we want to start
at the beginning of the API response.  The limit gives us how many we want at a
time.  So with an offset of 0 and a limit of 20, this will give us the first 20
businesses that meet our search criteria.  We loop again and as long as the
response["businesses"] array is not empty we continue on (we know there are a
lot more than 20 results so it loops again).  This time, offset has increased by
20 so we start at the 21st element and get another 20.  We keep doing this
until we have all of them.  

From there you can do whatever you'd like with all that data by looping over the resp array we've been appending the responses into.  I actually needed to put these into a CSV which I trust you already know how to do. Hope that was helpful!

You can find a gist of the entire code <a href="https://gist.github.com/3c899bbf8033be08c615">here</a>

{% gist 4321346 %}
