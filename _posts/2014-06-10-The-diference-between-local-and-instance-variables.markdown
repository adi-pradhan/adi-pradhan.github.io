--- 
layout: post 
title:  "The difference between local and instance variables" 
date:  2014-06-10 9:45:00 
categories: Ruby OOP
---

Shortest possible explanation , with a demonstration

Local variables are accesible only in the local scope i.e. method or function e.g. 

{% highlight ruby %}
class Book
  def initialize
  	name = "Harry Potter and the Philosopher's Stone"
  end

  def print_name
     puts name # this will fail with a Variable Not Found error
  end
end
{% endhighlight %}

The local variable name above is not accesible in the print_name method. 

To get a variable whose scope is the entire object instance, we need an instance variable

{% highlight ruby %}
class Book
  def initialize
  	@name = "Harry Potter and the Philosopher's Stone"
  end

  def print_name
     puts @name # this will work and print out the right value
  end
end
{% endhighlight %}