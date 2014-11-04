---
layout: post
title: "The TNT Journey - Part 6"
date: 2014-11-01 21:06:27 +0530
comments: true
categories: ["latentview", "tnt"]
---
31 October 2014. 7 PM. Struggling because I don't have an eye for design and I didn't know what to do about the infographic. Struggling because I wasn't satisfied with the result I got with this. And that was when rescue arrived.

Deadline extension.

I have never been this happy about a deadline extension. These two extra days give me a lot of time to fix what I'd done. And to fix the unsatisfactory results I had, I had one choice - to change the logic I was using.

I had to start from scratch.
<!--more-->

The two days gave me a lot of time to fix the stats I was considering for the selection. Yeah, I had a semester practical exam at the end of those two days. But still, priorities. 

So first, there were two things that happened before the initial deadline that made me unhappy with my results.

* I couldn't get the genetic algorithm thing working. I had to manually pick the best players for each category.
* I had to settle on using just the basic stats I had to pick the teams.

I ended up with a decent All Star team - Watson, Amla, Kohli, AB, George Bailey, Kane Williamson, MSD, Andre Russell, Steyn, Rangana Herath and Anderson. But the Indian team I got had Praveen Kumar in it. Not Bhuvaneshwar Kumar, not anybody else who's ever bowled for India. I got a guy who's been "out of action" for quite a while. I knew this thing was messed up. But I didn't have a lot of time to fix it, so I went ahead with it.

So when I heard about the deadline extension, I knew had time to right these wrongs. I got to reading articles on Cricinfo about suggestions for new statistics (I can't believe I didn't do that before). So with help from a few friends who reviewed the teams I was generating and suggested new factors to consider (thank you Pranav, Lakshmi and Arjun), I picked a bunch of new factors to consider.

* Mike Hussey's "Magic Number": I read about this number that Mike Hussey suggested for comparing T20 batsmen. A good T20 batsman would have (Average + Strike Rate) > 160. This means, a batsman scores an average of 40 runs at a rate 120 runs in 100 balls is as valuable as a batsmen who scores an average of 20 at 140. I didn't try to judge ODI batsmen in terms of a set number like 160, but I fixed a mistake that I did the last time - add the stats rather than find their product. Normalize the stats to a scale based on the weight of the stat, and add them. 

* Milestone values : This number is suggestive of the batsman's ability to put up big scores. I used MongoDB aggregation to get a list of individual innings scores for each batsman. From this list, assign incremental scores to milestone innings (50-74, 75-89, 90-99, 100-124, etc.). Assign a 5-point score for the ratio of 50+ innings and total innings, and a 10+ score for the ratio of 100+ innings and 50+ innings. The sum of all these values gives the overall milestone value of the batsman.

* Estimated Runs Added (ERA): This number feels so Sabermetrics-like. It gives how much the batsman scores more than the average runs scored at that rate. For a given batsman's average and strike rate, find the number of balls he would take to score that average. Also, find the runs scored for the same number of balls on the overall dataset average strike rate. The difference between the two gives a batsman's ERA.
ERA = Avg– ((100 * Avg / SR) * (Total runs in dataset/Total balls in dataset))

* Over group analysis: I got this idea from an article on Cricinfo. The basic idea behind this is that a bowler's performance in different sections of the innings should be weighted differently. For example, a good economy rate in the death overs should be weighted more than a good economy rate in the middle overs. A team's innings is broken into 3 parts – the powerplay overs (overs 1-15), the middle overs (overs 16-40) and the death overs (overs 41-50). Using MongoDB aggregation, built collections with lists of runs conceded on each ball, and number of wickets taken in each section. For the runs conceded section, the total runs conceded (batsman runs + extras) is considered, thus redefining it as runs conceded to the team. For each bowler who has bowled a certain number of balls in each section, positive or negative scores were allotted for different stats compared to the overall average – dots/over, boundaries/over, economy rate, wickets/over. Weights were given depending on the over section. For example, more weight is given to dots/over in the death than in the middle overs. This basically considers that it is harder to bowl in the death than in any other point of the innings. 

With this improved set of stats, I was hopeful of better results in terms of the team I got. 

Analysis on the teams in the next post. The final post of the series.