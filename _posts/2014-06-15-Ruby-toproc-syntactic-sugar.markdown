--- 
layout: post 
title:  "Ruby's toproc syntactic sugar" 
date:  2014-06-15 9:45:00 
categories: Ruby Sugar toproc
---

Ruby has a lot of great idiomatic ways to doing common things. The problem is a lot of them seem reminiscent of crazy perl magic when you first see them... One of the nicest ones is the `&` or `to_proc` concept

{% highlight ruby %}

['this','is','a','collection'].each do |element|
	element.capitalize!
end

#['This','Is','A','Collection']

{% endhighlight %}

OK so thats already a nice easy way of doing things. Its clear and concise, however in Ruby there is an even easier way

{% highlight ruby %}

['this','is','a','collection'].map(&:capitalize)

#['This','Is','A','Collection']

{% endhighlight %}

Even less code ! But a bit more confusing... Whats going on here? 

Well `&` is Ruby's to-proc symbol meaning it converts a block to a proc. In this case it is used to create a lambda/proc for the map method and therefore apply `String#capitalize` to each element of the array