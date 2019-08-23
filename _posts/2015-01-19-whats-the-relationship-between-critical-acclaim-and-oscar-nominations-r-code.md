---
ID: 514
post_title: >
  What’s the relationship between
  critical acclaim and Oscar nominations?
  Practically none.
author: admin
post_excerpt: ""
layout: post
permalink: >
  http://www.omarwasow.com/2015/01/19/whats-the-relationship-between-critical-acclaim-and-oscar-nominations-r-code/
published: true
post_date: 2015-01-19 15:35:37
---
Reading David Carr's piece on <a href="http://www.nytimes.com/2015/01/19/business/media/why-the-oscars-omission-of-selma-matters.html">Why the Oscars’ Omission of ‘Selma’ Matters</a>, I was struck by this passage: 

<blockquote>The movie was completed near the end of the year, and the screeners came late and somewhat sporadically. Perhaps that partly explains why “Selma,” which was second to “Boyhood” in critical acclaim as measured by Metacritic, received just two nominations, for best picture and best song. 
</blockquote>

This got me wondering, was Selma an outlier? 

Curious to assess the relationship between critical commentary and nominations, I quickly collected some small data and plotted the relationship among films nominated in the major categories:

<blockquote class="twitter-tweet" lang="en"><p>What’s the relationship between critical acclaim and Oscar nominations? Practically none. <a href="http://t.co/LPfsRlZGKE">pic.twitter.com/LPfsRlZGKE</a></p>&mdash; Omar Wasow (@owasow) <a href="https://twitter.com/owasow/status/557247255892082688">January 19, 2015</a></blockquote> <script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

So, is Selma an outlier? David Carr appears to have missed one other film, Two Days, One Night, that rated slightly higher than Selma on Metacritic and received only one nomination. That said, both films appear to have gotten a raw deal when you compare critical reception to Academy Award nominations. More broadly, there doesn't appear to be much correlation between what critics like and recognition by the Academy.

As to the plot, there's lots of room for improvement so I've posted the data and code below.

<code>
# List of films drawn from: <a href="http://www.metacritic.com/feature/2015-oscar-nominations-87th-academy-awards">http://www.metacritic.com/feature/2015-oscar-nominations-87th-academy-awards</a>
# Number of Oscar nominations taken from above and wikipedia
# Fractional Oscar nominations (e.g., 8.75, 9.25 instead of 9) done to prevent overlapping labels
# Metacritic scores taken from individual film pages on meteoritic

# Possible improvements:
#  - List of films with Metacritic scores above ~69 with zero nominations
#  - Other data (say budget or date of release)
#  - Collecting larger sample of films (e.g., prior years)
#  - Excluding technical academy awards to make results more comparable 

raw_txt = "Film, Metacritic_Score, Oscar_Nominations
Boyhood, 100, 6 
Two Days One Night, 92, 1 
Selma, 89, 2
Birdman, 88, 8.75
Grand Budapest Hotel, 88, 9.25
Whiplash, 88, 5
Imitation Game, 72, 8
American Sniper, 72, 6
Interstellar, 74, 5.25
Foxcatcher, 81, 5
Inherent Vice, 81, .75
Gone Girl, 79, 1.25
Nightcrawler, 76, .75
Theory of Everything, 72, 4.75   
Still Alice, 72, 1
Wild, 76, 2
Into the Woods, 69,3
#The Judge, 48 ,1
"
#The Judge dropped due to way outlying Metacritic Score 

raw_data = textConnection(raw_txt)
raw = read.table(raw_data, header=TRUE, comment.char="#", sep=",")
close.connection(raw_data)

summary(lm(Oscar_Nominations~Metacritic_Score, data=raw))

p <- ggplot(raw, aes(x=Metacritic_Score, y=Oscar_Nominations, label=Film))

p + geom_text() + scale_y_continuous("Oscar Nominations", limits=c(0,10), breaks=c(0,2,4,6,8,10)) +  scale_x_continuous("Metacritic Score", limits=c(68,100)) + theme(axis.text=element_text(size=14), axis.title=element_text(size=14)) + geom_smooth(method=lm, se=TRUE)

dev.copy(device=pdf, "metacritic_oscars.pdf", width=10, height=6)
dev.off()

# To post to twitter, I converted .pdf to png outside of R</code>