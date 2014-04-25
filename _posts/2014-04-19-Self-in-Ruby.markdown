--- 
layout: post 
title:  "Self in Ruby" 
date:  2014-04-19 9:45:00 
categories: ruby OOP 
---

As a reminder to self (how meta...), here's a quick intro to `self` in Ruby

`self` is a simple concept, it's a reference to an object that changes depending on where self is called e.g. 

{% highlight ruby %}

self # main

class MyClass
	puts self # MyClass

	def MyClass.a_class_method  # this could also be self.a_class_method
		puts self #MyClass
	end

	def an_instance_method
		puts self # an instance of MyClass
	end

	module M
		puts self # MyClass::M because this module is encapsulated by MyClass
	end

end

{% endhighlight %}

What's really important to know is that `self` is the default receiver of messages (method calls).