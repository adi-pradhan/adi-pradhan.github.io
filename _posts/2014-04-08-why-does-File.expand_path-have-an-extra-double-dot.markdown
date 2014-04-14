---
layout: post
title:  "File.expand.path has an extra .."
date:   2014-04-08 9:45:00
categories: ruby 
---

While reading some source code on github I was stumped by the use of File.expand.path. Here's
a short summary in case anyone else had the same problem.

`File.expand.path(file_name,[,dir_string])` is a ruby class method that simply gets an 
absolute path from a given relative path. The ruby doc for this method is http://ruby-doc.org/core-2.1.1/File.html#method-c-expand_path

For example lets say our current directory is 
`/home/myuser/code` 
and I have a file in there called 
`find_my_location.rb`.
Then `ruby -e "puts File.expand.path('find_my_location.rb')"` will return 
`/Users/myuser/code/find_my_location.rb`

If you wish to find the absolute path of the currently executing script then simply use 
`File.expand_path(__FILE__)`

So far so good. Now what happens when you have a structure as below:
{%highlight bash%}
./bin/server # current file
./lib/server_test/server.rb # need the absolute path of this file
{% endhighlight%}
That is you are executing `./bin/server` and wish to get the  `./lib/server/test/server.rb`
The correct answer is 
{%highlight ruby%}
# in ./bin/server
File.expand_path('../../lib',__FILE__)
{% endhighlight%}

But __why__ is there an extra `..` ? The first `..` indicates the parent of the `__FILE__` therefore to reach
. the necessary prefix is `../../` 

So the first `..` is used to indicate the parent of the argument i.e. the containing folder of the `server` file! 
