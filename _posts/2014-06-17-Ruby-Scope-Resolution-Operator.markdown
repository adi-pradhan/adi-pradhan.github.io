--- 
layout: post 
title:  "Ruby scope resolution operator without a prefix. The double colon with a prefix" 
date:  2014-06-17 9:45:00 
categories: Ruby Double-Colon 
---

Ruby's scope resolution operation `::` the double-colon is very straightforward to use:
{% highlight ruby %}
module A
  modules B 
  	MY_CONSTANT = 'test'
  end
end

puts A::B::MY_CONSTANT # 'test'

{% endhighlight %}

Great, that's a well namespaced constant. But, what if you need to refer to a constant on the outer namespace (global namespace)
from the module ? 

Easy...

{% highlight ruby %}
MY_CONSTANT = 'on the global scope'
module A
  modules B 
  	MY_CONSTANT = 'test'
  	puts MY_CONSTANT 	   # returns 'test'
  	puts A::B::MY_CONSTANT # returns 'test'
  	puts ::MY_CONSTANT	   # returns 'on the global scope'
  end
end

puts A::B::MY_CONSTANT # 'test'
puts MY_CONSTANT 	   # 'on the global scope'
puts ::MY_CONSTANT     # 'on the global scope'
{% endhighlight %}