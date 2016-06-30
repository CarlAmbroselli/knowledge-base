---
layout: post
title:  "Get Mac resolution in terminal"
categories: [terminal]
comments: true
---

I have a folder for scripts in `~/.bin` and added that folder to my `$PATH`. I put the following script into `~/.bin/resolution` and made executable with `chmod +x ~/.bin/resolution`.

This allows me to quickly get the current resolution of the connected screens (including the interal MacBook screen) by just running the command `resolution` in my terminal.

~~~
#!/bin/bash
system_profiler SPDisplaysDataType | grep Resolution | sed -e 's/^[^R]*//g'
~~~
