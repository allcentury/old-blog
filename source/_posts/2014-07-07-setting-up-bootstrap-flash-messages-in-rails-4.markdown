---
layout: post
title: "Setting up Bootstrap Flash Messages in Rails 4"
date: 2014-07-07 10:12:18 -0400
comments: true
categories: 
---
<a href="http://getbootstrap.com/components/#alerts">Bootstrap Alerts</a> are a wonderful way to enhance your user experience by giving them helpful hints with colors that scream success or failure!  Sometimes I'm able to use all of the available alert types in an app but it takes a bit of configuration.  There are many ways to do this but I find the best way (for me) is to create a simple function in my helper file that can reference each of the alert css classes as needed. 

For example, Bootstrap's 'success' class needs your HTML to look like:

```html alert.html
<div class="alert alert-success">
  ...
<div>
```
It should look something like this:
<img src="http://i.imgur.com/RqoXnFG.png">

Ok so how do we set this up in our Rails app?  First, let's add the css class information to `app/helpers/application_helper.rb`

```ruby application_helper.rb
module ApplicationHelper
  def flash_level(type)
    levels = {
      "notice" => "info",
      "success" => "success",
      "alert" => "warning",
      "error" => "danger"
    }
    levels[type]
  end
end
```

Now we just need to reference this in `app/views/layouts/application.html.erb` like so:

```ruby application.html.erb
<% flash.each do |name, msg| %>
  <div class="alert alert-<%= flash_level(name) %>" >
    <%= msg %>
  </div>
<% end %>
```

This block of code is pretty simple, as each flash message gets passed into the block, we simply append the css class we stored in the helper into the class.  Currently in Bootstrap 3 all alerts start with "alert" then the alert level followed, such as `alert-success`.  If Bootstrap decides to change any of the flash css information, it's a simple fix for us and doesn't require any funky logic!
