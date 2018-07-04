+++
title = "My experience getting started with Hugo"
description = ""
tags = [
    "go",
    "golang",
    "hugo",
    "development",
]
date = "2014-07-03"
categories = [
    "Development",
    "golang",
    "blogging",
    "hugo",
    "git"
]
menu = "main"
+++

It looks like all tech blogs need to start with posts about how the blog was built.
So here goes.

If you haven't seen the footer I decided to go with [Hugo](http://gohugo.io/) to create my blog, it seemed fairly easy and created a static site that I can run on github pages or AWS S3. A recurring theme on this blog will probably be how terrible I am as a developer so this is really a must have feature. That said, Hugo also has a lot of tinkering availble so long as you're happy sticking to a static site, hopefully I'll make use of this and actually get better at CSS/HTML... \<insert laughing image\>

To replicate what I've done you're going to be deploying to a github repo and the Hugo instructions on this method are pretty straightforward. [Here's a link](https://gohugo.io/hosting-and-deployment/hosting-on-github/)

Less waffle, more detail. In reality it's taken so long to get this working, I probably should have written it myself from scratch. I'm going to write down the gotchas I had so that you don't come against them later on, bear in mind as well that if you use a different theme to me, my theme is [Hucore](https://github.com/mgjohansen/hucore), you'll probably have some different issues.

## Issue 1: public

I didn't set add the `public` directory as a submodule, when I went to publish my site for the first time I was already so far in to the guides that it took ages to unpick what on earth was going on. Make sure to do this from the beginning.

## Issue 2: theme

When I installed the theme I followed the instructions that the theme gave me and just ran `git clone` into the `themes` directory. When it came to time to commit into github, which is where I plan on keeping the source for the site, I found myself in a position where the site wouldn't build because git wouldn't commit the directory properly, not to mention that any changes I made to the theme wouldn't commit.

Getting this right meant forking the theme so that I was able to make changes to the source and then adding the theme as a git submodule. You can skip the forking if you're not planning on making any changes to the theme.

## Issue 3: Styling

The favicon in Hucore is replaced by editing `layout/partials/nav.html` which if you didn't fork the theme needs to be copied from `themes/hucore/layout/partials/nav.html`. To get my icon working I used my [favourite icon generator](https://realfavicongenerator.net/). You can unzip the contents into `static` and change the URI for the `<link>` tags to `{{ .Site.BaseURL }}`.

The top nav doesn't fit long blog names very well if you're working on a small window, I'm doing this in a VM so that I don't have to do it on Windows ;), copy `nav.html` like above and you can seperate the container `<div>` just copy all the classes and the `<nav>` tags.

These are probably particular to the Hucore theme but took me a while to solve, mostly because I'm bad at html.

I hope this all helped and that my writing wasn't too bad!
