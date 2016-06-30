---
layout: post
title:  "Extract any file with a single command"
categories: [terminal]
comments: true
---

I have a folder for scripts in `~/.bin` and added that folder to my $PATH.

Having the following script placed in `~/.bin/extract` and made executable with `chmod +x ~/.bin/extract` allows me to use the same command to extract any file like  `extract file.zip` or `extract file.tar.gz`. If you are missing an executable used by this script just install it with [homebrew](http://brew.sh/){:target="_blank"}.

~~~
#! /bin/bash
if [ -f $1 ]
then
  case $1 in
      *.tar.bz2)  tar -jxvf $1                        ;;
      *.tar.gz)   tar -zxvf $1                        ;;
      *.bz2)      bunzip2 $1                          ;;
      *.dmg)      hdiutil mount $1                    ;;
      *.gz)       gunzip $1                           ;;
      *.tar)      tar -xvf $1                         ;;
      *.tbz2)     tar -jxvf $1                        ;;
      *.tgz)      tar -zxvf $1                        ;;
      *.zip)      unzip $1                            ;;
      *.ZIP)      unzip $1                            ;;
      *.pax)      cat $1 | pax -r                     ;;
      *.pax.Z)    uncompress $1 --stdout | pax -r     ;;
      *.rar)      unrar x $1                          ;;
      *.Z)        uncompress $1                       ;;
      *)          echo "'$1' cannot be extracted/mounted via extract()" ;;
  esac
else
  echo "$1 is not a valid file"
fi
~~~
