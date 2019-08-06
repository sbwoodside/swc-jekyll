---
layout: post
title: How to make emacs understand nginx files
---

I started using `emacs` about 20 years ago, but I never mastered it. I learned most of the text editing keys, but I never bothered to understand modes, commands, modules, or how to use it to read email, surf the web, or emulate videogames.

Recently I started to spend a lot more time managing servers and got frustrated that there wasn't a built-in mode for nginx configuration files. I googled it, but just try to understand most of the instructions out there on how to use `emacs`. They tend to assume a lot of prior knowledge and there is unfortunately more than one way to do it. That leads to confusion.

As it turns out, `emacs` now has a pretty good package management system. So that simplifies matters a lot. You still have to figure out that there's a few different package repositories, and which one to use. But, once you get over that hurdle, installing new file modes (i.e. syntax highlighters and formatters for different languages) is pretty easy.

First, install `emacs`. Then:

    sudo emacs /etc/emacs/site-start.el
    
Paste in the code here: https://melpa.org/#/getting-started

    (require 'package) ;; You might already have this line
    (add-to-list 'package-archives
                 '("melpa" . "https://melpa.org/packages/"))
    (when (< emacs-major-version 24)
      ;; For important compatibility libraries like cl-lib
      (add-to-list 'package-archives '("gnu" . "http://elpa.gnu.org/packages/")))
    (package-initialize) ;; You might already have this line

Save and exit.

## nginx-mode

To get nginx pretty-printing and indentation, do this to install `nginx-mode`:

    sudo emacs
    M-x package-list-packages
    C-s nginx RET
    i
    x

Then you can switch into `nginx-mode` with `M-x nginx-mode`. 
You can make it recognize the sites-enabled files automatically by looking at the <a href="https://github.com/ajc/nginx-mode#commentary">commentary here</a>.
