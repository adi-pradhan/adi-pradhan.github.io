--- 
layout: post 
title:  "A short guide to tmux awesomeness" 
date:  2014-04-16 9:45:00 
categories: linux 
---

Tmux or `Terminal Multiplexer` may be one of the coolest and most
productive utilities out there.

It allows users to have multiple windows and panes and rapidly shift
between them using keyboard shortcuts.

Below I have 3 panes, one with `man tmux` , one with `top`  and another waiting for me to 
type something in !

![A tmux setup with 3 panes]({{ site.url }}/assets/tmux.png)

Tmux is a little tricky to get the hang of so I've summarized how to use
it below specifically if all you want to do is use multiple panes and
switch between them:

Install tmux using your favorite package manager

`yum install tmux` or `apt-get install tmux`

you may need to `sudo` before using those commands

Verify tmux is installed by `tmux -V`. This should give you a version
number.

Start tmux using the command `tmux`

This shouldn't change anything apart from a row at the bottom of your
shell

Tmux is manipulated using the prefix key `CTRL-b` , hitting this
combination tells tmux that the next command is aimed at tmux and not
the shell

You have to press `CTRL-b` together first, then release and press the
next key:

To make a vertical split pane press `CTRL-b` then press `%` i.e. the
percent sign using `SHIFT-5` on US keyboards

To make a horizontal split pane press `CTRL-b` and then `"` i.e. the
double quote character

To change the pane in focus press `CTRL-b` and use the arrow keys to
move the focus.

And finally, to get help press `CTRL-b` and then `?`

Now if you're using PuTTy as a terminal emulator , you may see  `â` as
the tmux pane separator/divider instead of a line. The issue is the
encoding, set your $LANG environment profile in your `~/.bash_profile` by adding the line

`export LANG=en_US.UTF-16`

that should fix it. 

There's a lot more to tmux but i think even these few instructions are enough to make a 
massive productivity jump