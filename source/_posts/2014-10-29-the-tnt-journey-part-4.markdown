---
layout: post
title: "The TNT Journey - Part 4"
date: 2014-10-29 09:17:35 +0530
comments: true
categories: ["latentview", "tnt"]
---
When you have exams and an interesting problem that you have to complete in a few days, it's not too cool to go down with a fever. These next couple of days are going to be a blaze with all the work. I need to get this done with.

Before picking the teams, I needed a way to visually represent the data I had so far. I needed to have the graphs look beautiful, and also easy to generate.

Enter [Plotly](https://plot.ly)
<!--more-->

I think of it more as, the GitHub of Graphs.

I heard about Plotly during PyCon India 2014. I found it really interesting and decided to use it for any interesting project I had to work on (also because I put a Plotly sticker on my laptop, so I had to use it because I donated laptop real estate to it). Just as I was looking for ideas of things to work on, I came across TNT, so I decided that it might be a good time to start using Plotly. 

It was so much easier than I thought.

I decided to use the [Plotly Python API](https://plot.ly/python) for generating some visual representations of the data. The documentation is very extensive, and the examples given are usually more than enough to get you going. The best part is how easy it is to collaborate and work on the graphs across languages/tools - when you have the link to your graph, all you have to do is add a .py or .r or .js or .m to work with the graph in Python, R, Javascript or Matlab. The link with .png gives the graph as an image, and .html gives an iframe that embeds the graph in a web page. How cool is that !

I decided to go with using iframes mainly because I wouldn't have to edit the webpage every time I edited the graph. It would be really useful when I worked on my data often. 

So I went ahead and built histograms for each of the 7 batting/bowling statistics that I mentioned in the [previous post](http://periphrastic-prolixity.herokuapp.com/blog/2014/10/26/the-tnt-journey-part-3/). 

Starting off with the batting stats.

* Runs per wicket

<iframe frameborder="0" seamless="seamless" scrolling="no" src="https://plot.ly/~AlexMathew/1.embed" width="600" height="400"></iframe>

* Runs per 100 balls

<iframe frameborder="0" seamless="seamless" scrolling="no" src="https://plot.ly/~AlexMathew/2.embed" width="600" height="400"></iframe>

* Pinch hitting rate 

<iframe frameborder="0" seamless="seamless" scrolling="no" src="https://plot.ly/~AlexMathew/3.embed" width="600" height="400"></iframe>


The bowling stats.

* Overs to concede 100 runs

<iframe frameborder="0" seamless="seamless" scrolling="no" src="https://plot.ly/~AlexMathew/4.embed" width="600" height="400"></iframe>

* Wickets per 10 overs

<iframe frameborder="0" seamless="seamless" scrolling="no" src="https://plot.ly/~AlexMathew/5.embed" width="600" height="400"></iframe>

* Overs to concede 10 boundaries

<iframe frameborder="0" seamless="seamless" scrolling="no" src="https://plot.ly/~AlexMathew/6.embed" width="600" height="400"></iframe>

* Overs to concede an extra

<iframe frameborder="0" seamless="seamless" scrolling="no" src="https://plot.ly/~AlexMathew/7.embed" width="600" height="400"></iframe>

Now, this is useful to notice how I can't use the entire player dataset to generate my team, because it would end up skewed in favour of players who rarely played. A player who has bowled only one over in the given timeframe, and conceded just 1 run along with taking a wicket will have statistics like 100 overs to concede 100 runs and 10 wickets per 10 overs - which is obviously messed up. So I need to set a minimum number of innings that a player should have batted or bowled in, if the player has to be considered for the team. I'm setting that number at 23 - I'll see how it turns out and make changes if I have to. 

I'll continue using Plotly to represent other statistics of the generated team. And that is what I'll have to start working on now.
