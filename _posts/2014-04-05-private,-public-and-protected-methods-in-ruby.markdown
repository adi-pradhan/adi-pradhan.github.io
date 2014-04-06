---
layout: post
title:  "Private, Public and Protected Methods in Ruby"
date:   2014-04-05 9:45:00
categories: ruby OOP methods 
---


Ruby's method access control is used to define how other objects may invoke messages on the target class.

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

You can also call a `private` method to define what methods in a class are private
{% highlight ruby %}
private :a_private_method, :another_private_method
{% endhighlight %}

The purpose of making a method private is to ensure it can NOT be called with an explicit reciever. It must be called when self is an instance of the class i.e. 

{% highlight ruby %}
def public_method
  private_method # here the public method invokes the private method (notice there is no receiver, or receiver=self)
end
{% endhighlight}

By tagging a method as private you are saying only an instance of the class can send this message to itself.

Protected methods are less strict, instances of the class can call this method on other instances (as the receiver)