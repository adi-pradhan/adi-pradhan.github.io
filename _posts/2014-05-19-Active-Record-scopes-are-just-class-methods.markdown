--- 
layout: post 
title:  "Active Record scopes are just class methods" 
date:  2014-05-19 9:45:00 
categories: Rails scopes Ruby class methods Active Record
---

Rails used an ORM (Object Relational Mapper) called Active Record that has a lot of cool features, one of these is scopes.

A scope is essentially a SQL `WHERE` clause and it is written as below
{% highlight ruby %}
class Book < ActiveRecord::Base
	scope :recent, -> { where('finished_on > ?',2.days.ago)}
end
{% endhighlight %}

so running `Book.recent` in  `rails console` or in your app will give you all Books with the recent value being within the
last two days.

But what is a scope? If you think of each row in the Books table as an instance of the `Book` class. Then
the scope is simply a class method. So writing the scope as below is almost equivalent

{% highlight ruby %}
class Book < ActiveRecord::Base
	def self.recent
		where('finished_on > ?',2.days.ago)
	end
end
{% endhighlight %}

almost... there are a few subtle differences