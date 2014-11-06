---
layout: post
title: "The TNT Journey - Part 7"
date: 2014-11-03 04:56:57 +0530
comments: true
categories: ["latentview", "tnt", "plotly"]
---
A new approach. Better results.

Here, I'll share the team I generated based on the stats I used, and my insights on the numbers involved.

The grand curtain call to this series.
<!--more-->

These were the teams generated - 

ALL STAR XI :
Shane Watson, Hashim Amla, Virat Kohli, Kumar Sangakkara, AB de Villiers, MS Dhoni, Shahid Afridi, James Tredwell, Dale Steyn, Saeed Ajmal, James Anderson

BENCH - James Faulkner, Andre Russell, Rangana Herath, Jos Buttler


INDIA XI :
Virender Sehwag, Shikhar Dhawan, Virat Kohli, Rohit Sharma, Suresh Raina, MS Dhoni, Ravindra Jadeja, R Ashwin, Bhuvaneshwar Kumar, Amit Mishra, Mohammed Shami

BENCH - Gautam Gambhir, Manoj Tiwary, Vinay Kumar, Umesh Yadav


I made a bubble chart comparing batsmen's ERA and milestone values, and multiple bar charts to compare bowler stats across various over groups. (Thank you, [Plotly](http://plot.ly))

<iframe frameborder="0" seamless="seamless" scrolling="no" src="https://plot.ly/~AlexMathew/16.embed" width="600" height="400"></iframe>

<iframe frameborder="0" seamless="seamless" scrolling="no" src="https://plot.ly/~AlexMathew/23.embed" width="600" height="400"></iframe>

<iframe frameborder="0" seamless="seamless" scrolling="no" src="https://plot.ly/~AlexMathew/24.embed" width="600" height="400"></iframe>

<iframe frameborder="0" seamless="seamless" scrolling="no" src="https://plot.ly/~AlexMathew/25.embed" width="600" height="400"></iframe>

<iframe frameborder="0" seamless="seamless" scrolling="no" src="https://plot.ly/~AlexMathew/27.embed" width="600" height="400"></iframe>

Insights about the teams and the related stats :

* AB, MSD and Kohli are ridiculously valuable to the team. They put up big scores and they do it at an excellent strike rate. People like Sanga and Rohit Sharma are the kind of people who'd play an average-paced innings, but put up a score to set the tone of the innings. Shahid Afridi is a classic pinch hitter (any cricket fan can vouch for that). Very few milestone innings, but he adds a lot of value in terms of his scoring rate. 

* Cricket nowadays seems to revolve around the quality of the wicketkeeper-batsman in the team. When I considered the overall batting performance ratings to pick the batsman for the team, there were 4 keepers in the top 10 - MSD, Sanga, Jos Buttler and Quinton de Kock. Granted Buttler and de Kock are relatively new and haven't played a lot, but the fact that they start off immediately as valuable batsman shows the value of a good batsman who can perform well behind the wickets.

* It turns out Amit Mishra has been India's most valuable bowler. In terms of pure wicket taking ability, he really stands out above the crowd of Bhuvi-Shami-Ishant-Umesh Yadav and the others. 

* Any Indian cricket fan would already know this - Indian bowlers are pathetic in the death overs. After Zaheer and Ajit Agarkar at his peak, India has almost never had a good death-over bowler. This fact is very obvious from these graphs - Shami and Bhuvi get tonked in the death. Ishant Sharma and Umesh Yadav - who didn't feature in the main XI - don't fare too well here either.

* Dale Steyn is the MVP among bowlers. By quite a margin, actually. James Tredwell has had good performances, but the problem is the limited number of matches he has played. James Anderson is a classic strike bowler - a brilliant opening spell marked by an excellent economy rate and some wickets, and a death-over spell where runs flow but a lot of wickets fall. 

You can obviously argue with a lot of these numbers. Your argument will be justified because there are flaws in the approach taken to get these teams.

* It doesn't consider form or the venue where they played. This would change a lot, especially with the Indian XI. Viru wouldn't be in the running for the spot at the top, and I wouldn't have had to deal with Praveen Kumar and Irfan Pathan almost making the cut. Also, Amit Mishra's value may have dropped if you considered overseas performances. An intuitive look at the team will give some more credit to new players who are putting up good performances - Ajinkya Rahane and Ambati Rayudu in place of Sehwag and Rohit Sharma.

* It doesn't considering fielding/wicketkeeping performances. Picking the primary keeper for this team was solely on the basis of their batting contribution. This issue came up because there was no way to know the total number of matches they had played - I discussed that situation in [Part 3](http://periphrastic-prolixity.herokuapp.com/blog/2014/10/26/the-tnt-journey-part-3/) of this series. It just assumes that everyone in the modern cricketing world is a good fielder, and they wouldn't even be playing if they were poor fielders.

* There are definite limitations on the stats I have considered. You could argue there is some metric that would show that someone else is better than someone on these teams. I really need to learn more about statistics.

So that's it from me. This has been an amazing 3 weeks with this problem. Somehow, being awake felt worthwhile. 

Thank you LatentView.
