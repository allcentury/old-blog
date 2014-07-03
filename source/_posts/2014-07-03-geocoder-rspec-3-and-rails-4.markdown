---
layout: post
title: "Geocoder, RSpec 3 and Rails 4"
date: 2014-07-03 13:45:23 -0400
comments: true
categories: 
---

I've been working on a project that utilizes the Geocoder gem and as an avid
TDD'r I was trying to prevent my tests from hitting Google's servers a million
times.  Frankly I run my test suite a lot throughout the course of a day so
having this was necessary because I hit Google's limits a few times.

Here's my set-up which somewhat similar to Samuel Mullen's with more of a focus on RSpec.

`Gemfile`:
```ruby Gemfile

group :test do
  gem 'fakeweb'
end
```

Create a new file, I put mine under `spec/support` called `geocoder.rb`

```ruby geocoder.rb

google_json = <<-JSON
{
  "results" : [
  {
    "address_components" : [
    {
      "long_name" : "1600",
        "short_name" : "1600",
        "types" : [ "street_number" ]
    },
    {
      "long_name" : "Amphitheatre Pkwy",
      "short_name" : "Amphitheatre Pkwy",
      "types" : [ "route" ]
    },
    {
      "long_name" : "Mountain View",
      "short_name" : "Mountain View",
      "types" : [ "locality", "political" ]
    },
    {
      "long_name" : "Santa Clara",
      "short_name" : "Santa Clara",
      "types" : [ "administrative_area_level_2", "political" ]
    },
    {
      "long_name" : "California",
      "short_name" : "CA",
      "types" : [ "administrative_area_level_1", "political" ]
    },
    {
      "long_name" : "United States",
      "short_name" : "US",
      "types" : [ "country", "political" ]
    },
    {
      "long_name" : "94043",
      "short_name" : "94043",
      "types" : [ "postal_code" ]
    }
    ],
      "formatted_address" : "1600 Amphitheatre Pkwy, Mountain View, CA 94043, USA",
      "geometry" : {
        "location" : {
          "lat" : 37.42291810,
          "lng" : -122.08542120
        },
        "location_type" : "ROOFTOP",
        "viewport" : {
          "northeast" : {
            "lat" : 37.42426708029149,
            "lng" : -122.0840722197085
          },
          "southwest" : {
            "lat" : 37.42156911970850,
            "lng" : -122.0867701802915
          }
        }
      },
      "types" : [ "street_address" ]
  }
  ],
    "status" : "OK"
JSON

FakeWeb.register_uri(:any, %r|http://maps\.googleapis\.com/maps/api/geocode|, :body => google_json)
```

Once you have that, you simply need to use the new RSpec Rails helper, found in `spec/rails_helper.rb` and include this line near the top

```ruby rails_helper.rb
require Rails.root.join("spec/support/geocoder")
```
