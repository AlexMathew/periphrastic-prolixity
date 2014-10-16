---
layout: post
title: "The TNT Journey - Part 1"
date: 2014-10-16 14:58:04 +0530
comments: true
categories: ["latentview", "tnt"]
---
And so, the journey with TNT begins. A 175K+ row dataset. A new challenge.

Over the next few posts, I'll document the various facets of my approach to this problem. Part 1 - how do I get started ?

<!--more-->
I registered for the event a few days after I heard about it. I thought I'd give myself time to get some basic idea in place before I get started. So I took my time to read about various statistics that people proposed and how it'd help in finding the most efficient players. In my head, it felt like Brad Pitt and Jonah Hill discussing Sabermetrics. I loved how people were crunching numbers to produce evidence of how the statistic they proposed was effective. It seemed simple enough - work with their averages and strike rates and other basic statistics. With the expected basic idea in place, I registered for TNT, and later that day, I got the link to the dataset. Downloaded the file, unzipped it and opened the Excel sheet. And then the bomb dropped.

Ball-by-ball data.

Somehow, I didn't expect that I would have to work with ball-by-ball data. In its native form, ball-by-ball stats are pretty useless (unless you're analyzing run rate patterns and everything). So before getting to work with various performance measures, I had to put the available data together into cummulative stats.

I had a CSV file to work with. I had to pick my weapon to get started. I had a few options. 

R. I'd always wanted to get started with learning R. I never found a compelling reason to get around to working with it. This seemed like a very good starting point. But I didn't want to learn something from scratch for this. I thought it'd be a low-efficiency move to tread into unfamiliar territory, just to work with this dataset. So R, maybe later. Ruled out for now.

Pandas. Familiarity with Python, check. An interest to work with the data side of Python, check. But Pandas is very vast. Getting a base with NumPy to just get started is very hard. So SciPy stack, sometime soon, but not now. Ruled out for now.

I had a large dataset that I had to break into cummulative stats of each player. And I needed somewhere to store it. I would use a database anyway, so why not use it to also aggregate the data the way I need it ? And that was option 3.

MongoDB. I had done some basic work with MongoDB. The M101P course (which, even after 3 attempts, I haven't been able to finish) gave me a decent base with the CRUD and aggregation operations. 175K row dataset - bring out the aggregation framework !

Importing the data into a DB was easier than I thought.

```
$ mongoimport --db tnt --collection odi --type csv --file ODI.csv --headerline 
```

And that was done. Easy stuff.

The hard part was writing aggregation commands to do the required grouping. It's sort of like writing regular expressions - extremely hard, very annoying, but so damn powerful. After a lot of reference from the MongoDB docs and StackOverflow, I managed to get the stats I needed. For example, to get the total runs that a batsman scored.

``` javascript MongoDB aggregation to find total runs scored
db.odi.aggregate([{ $group: {_id: "$Batsman", Runs: { $sum: "$Runs Batsman" } } }, { $sort: { "Runs": -1 } }])

``` 

Some easy ones and some hard. And I managed to get the stats I needed. 

Now, step 2. I need to put this together and build some performance measures.

Part 2 of this series will be up when I have some significant progress on that front.
