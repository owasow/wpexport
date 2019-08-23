---
ID: 643
post_title: >
  Macros for quickly creating image slides
  in Latex + Beamer
author: admin
post_excerpt: ""
layout: post
permalink: >
  http://www.omarwasow.com/2019/02/09/macros-for-quickly-creating-image-slides-in-latex-beamer/
published: true
post_date: 2019-02-09 11:30:23
---
Scott Cunningham recently <a href="https://twitter.com/causalinf/status/1093859420013060096">tweeted</a> about the hassle of resizing slides in Beamer: 

<blockquote>One place where PPT>Beamer is when you have 650 slides and have to keep adjusting the scale of an image. Compile, check, compile, wait 20 seconds, repeat 5 times, give up.</blockquote>

This always bugged me, too, until I found some basic `macros' to generate image slides in Latex with one line of code. I <a href="https://twitter.com/owasow/status/1094244890849042432">tweeted</a> back:

<blockquote>A simple solution is to define some macros at the top of the document that create an image slide. I have three image sizes (full page, large & medium) and a few variations with/without titles and/or a source at the bottom. Images are always proportional & take one line of code.</blockquote>

And, in case it's of interest, here's a sample Beamer file with those macros.

<a href="http://omarwasow.com/beamer_image_slide_macros.zip">Zip file with sample Beamer slides and macros</a> to create image-heavy slides using one line of code.

...

<a href="https://twitter.com/owasow/status/1094247182079873024">Lastly</a>:

<blockquote>That said, I'm currently migrating slides from Latex / Beamer to R Markdown / Xaringan and digging 1/ speed 2/ ease of braiding together code/output/highlights for teaching 3/ ease of integrating web media (youtube, polls). See <a href="https://github.com/yihui/xaringan">https://github.com/yihui/xaringan</a></blockquote>