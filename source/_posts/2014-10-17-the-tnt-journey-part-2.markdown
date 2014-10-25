---
layout: post
title: "The TNT Journey - Part 2"
date: 2014-10-17 00:02:10 +0530
comments: true
categories: ["latentview", "tnt"]
---
Step 1 : Get cummulative statistics. [Done](http://periphrastic-prolixity.herokuapp.com/blog/2014/10/16/the-tnt-journey-part-1/). 

Now I need to find a way to measure the performance of these players during this period. Several people have written about different statistics to do this. I need to pick the best ones for the problem I have at hand.
<!--more-->

Aggregation worked beautifully. I got the cummulative stats I needed to work with. Now I have to put this into a new collection and I'm all set to go. Except, it wasn't that easy. Updating a collection with results from the aggregation pipeline is pretty hard. Looping through the results is too inefficient. After some research (read, StackOverflow), I found the $out pipeline stage. Seemed like just what I needed. I gave it a shot and got this.

```
"errmsg" : "exception: Unrecognized pipeline stage name: '$out'"
```

Roadblock ! Turns out $out is a new addition in MongoDB 2.6 and I was working with 2.4. So before any more progress could happen, an update had to happen. 

While I waited for the 100+ MB file download to complete (I have bad internet - 100MB is a big deal), I read some Quora answers and research papers on performance measures. Now I had to pick the ones that gave the most efficient results. 

I needed some proper measures to judge how useful a player is on a team. It's cricket, so a player can contribute to a team in many different ways. He could be a batsman who plays the bulk of the innings to set up the score, or he could be a batsman who faces around 15 or 20 balls to make a quickfire 30. He could be the strike bowler who takes 2 or 3 wickets in his qouta of 10 overs, or he could be the bowler who restricts the opponents' run flow by conceding only at around 3 runs an over. 

So what statistics would I have to consider ?

* Batting average : Runs scored per out. Undoubtedly, one of the most argued about statistics in cricket. And for valid reasons. The batting average ends up extremely skewed in favour of players who come lower down the order, because of the higher probability that they'd remain not out. 

* Strike rate : Runs scored per 100 balls. I remember watching cricket at a time when a strike rate of around 80 was the trademark of a "blazing innings". Times have definitely changed. Higher strike rates are a major focus in batting line ups.

* Batting pinch hitting rate : A very good idea I got out of [this Quora answer](http://www.quora.com/What-new-statistical-measures-could-make-cricket-better-in-terms-of-player-evaluation-and-viewer-experience/answer/Thomas-Foster). Boundaries have a huge impact on the flow of a match. It switches momentum, leads to the fielding setup getting shuffled, and so much more. This can be improved a little by giving a higher weightage to sixes (because sixes are awesome !). 

* Bowling average : Runs conceded per wicket taken. The lower, the better. Pretty efficient stat to work with.

* Bowling strike rate : Balls bowled per wicket. Because strike bowlers strike often. 

* Bowling pinch hitting rate : If it can be used to quantify a batsman's performance, it can be used for bowlers too. Batsmen want to score boundaries, bowlers should make sure they can't.

I need to find a way to work with all of these numbers together. And there should be an efficient way to strike a balance. Hashim Amla may not be the quickest scorer, but he definitely scores a lot. James Anderson has an average economy rate, but he's one of the best strike bowlers in the world. Normalize, combine these stats into one index - I need to see what works best. 


In other MongoDB news, it turns out $out is not what I need. I need to combine the results from multiple aggregation commands into one collection, but $out puts the result from one aggregation command into one collection. So I need to move back to my original option of looping through the results. Fire IPython, ```import pymongo``` and get to work.

Now that I have player-wise statistics, I need to find the most efficient way to quantify their overall performance and pick the best performers. 

Part 3 may take a while to come out. I'll work on some options and make one grand update on my progress.
