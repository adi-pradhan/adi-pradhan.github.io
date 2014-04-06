---
layout: post
title:  "Private, Public and Protected Methods in Ruby"
date:   2014-04-05 9:45:00
categories: ruby OOP methods 
---


Ruby's method visibility is used to define how other objects may invoke messages on the target class.

Loquacious languages like Java require each class and method to describe whether they are `public` or `private` 

{% highlight java %}
public Class Test Class{
	public static  void myPublicMethod( String inputString){
		// Allow other objects invoke this method i.e. send this my message to this object as the receiver.
	}

	private static void myPrivateMethod( String inputString){
		//Do Private Things within the context of the object
	}
}
{% endhighlight %}

Ruby simplifies this by making the default access on classes and methods public. If you don't specify any access modifier, everything is public.

{% highlight ruby %}
class TestClass
	def test_method
		puts "In the public method."
	end
end
{% endhighlight %}

Ruby makes it very easy to modify acces of the methods. Instead of specifying acces of each method, you call an access modified and all the method following that have the specified access i.e. Simply call `protected` or `private` and the following methods will be protected or private respectively.

{% highlight ruby %}
class MyTestClass
	def public_method
		puts "in the public method"
	end

	protected
	def protected_method
		puts "in the protected method"
	end

	private
	def private_method
		puts "in the private method"
	end
end
{% endhighlight %}


