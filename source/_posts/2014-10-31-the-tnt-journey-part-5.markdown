---
layout: post
title: "The TNT Journey - Part 5"
date: 2014-10-31 00:32:23 +0530
comments: true
categories: ["latentview", "tnt"]
---
With all the work looking at the player side of stuff, I didn't spend too much time on the venue-based side of the problem. So I decided to get that done. What can sides expect in Australia and New Zealand ? 

[Plotly](http://plot.ly) continues to impress with its usefulness.
<!--more-->

I couldn't come up with any really useful statistical measure to judge the performance in a particular venue, so I decided to go with three basic numbers - runs per 50 overs, wickets per 50 overs and boundaries per 50 overs - and put them in a 3D scatter plot (which turned out to be pretty easy with Plotly). 

It was back to MongoDB's aggregation framework to put this together. I went with the same workflow that I had with aggregating player data - write the aggregation commands, use a Python script to create a new collection with all the data. 

There were 89 unique venues in the given dataset. However, we couldn't go with the entire set because 30 of those venues hosted only one match, and one match is definitely not enough to observe a pattern. For example, there was only one match played at the Chinnaswamy Stadium and batsmen went all berzerk during that match - that also included Rohit Sharma's 209. But not all matches at the Chinnaswamy produce 600+ run spectacles. So there should be a minimum number of matches that a venue should have hosted if it has to be considered. Going with a minimum of 3 matches, we have a list of 40 venues (which notably exclude MAC, Wankhede and Eden Gardens). 

Working with these 40 venues, we set up a collection which contains the three stats that we are considering for each venue. Now it's just a matter of setting up the 3D scatter plot on Plotly. Since we are grouping by country, we need the country that the venue is located in. This was the annoyingly hard part - manually finding the country.

Now with some basic statistics on the data I have, and the generated 3D scatter plots, we can make some conclusions.

The scatter plot with all the countries which have venues in the dataset.

<iframe frameborder="0" seamless="seamless" scrolling="no" src="https://plot.ly/~AlexMathew/10.embed" width="800" height="800"></iframe>


Specifically with Australia and New Zealand.

<iframe frameborder="0" seamless="seamless" scrolling="no" src="https://plot.ly/~AlexMathew/11.embed" width="800" height="800"></iframe>


Across the 9 venues in Australia and New Zealand, the mean 50 over score increases by more than 10 to reach a score of 247, while the mean wickets/50overs remains almost the same - around 7.5. So expect many lower-order pinch hitters to make cameos. With 300+ scores becoming commonplace in ODI cricket, expect this mean 50 over score to increase over the course of the World Cup. Expect the average of 25 boundaries/50overs only from mediocre teams - if a team really has to make a mark, they'll have to step up that number. This World Cup is a funny mix because Australia is known for its longer boundaries, while New Zealand is known for its shorter boundaries. Batting fests are extremely possible in NZ, while Australia will host more balanced battles.

More insights soon.

I'll also continue working on finding a good way to build the team.
