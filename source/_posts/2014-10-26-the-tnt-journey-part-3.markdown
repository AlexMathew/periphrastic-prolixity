---
layout: post
title: "The TNT Journey - Part 3"
date: 2014-10-26 11:27:57 +0530
comments: true
categories: ["latentview", "tnt"]
---
Records, exams, assignments. The absolute worst time possible. Indian education will not improve till they get rid of this concept of maintaining a formal record book where you write unnecessary garbage. In the middle of all this, finding time to work on the TNT problem has been hard. But I've been reading, trying out stuff and making some gradual progress. And of late, I've approached this in a different way. Advice from a professor gave me an interesting way to go about this problem. Implementing has been hard, but the idea behind it is brilliant.
<!--more-->

"Don't look for individual best performers. Put the team together and see the overall rating of the team. Pick the best team, not a collection of the best players". I had never thought of that, really. The best players statistic-wise could all be batsmen, and I'd end up with a batting-heavy team with a poor bowling attack. So I had to find a way to strike a balance, by considering the team as a whole. And I considered using my professor's advice - genetic algorithms.

The idea was simple. From this [basic introductory post about GA](http://www.obitko.com/tutorials/genetic-algorithms/ga-basic-description.php),

> Algorithm is started with a set of solutions (represented by chromosomes) called population. Solutions from one population are taken and used to form a new population. This is motivated by a hope, that the new population will be better than the old one. Solutions which are selected to form new solutions (offspring) are selected according to their fitness - the more suitable they are the more chances they have to reproduce. 

I found a bunch of research papers, where people used GAs to do this exact thing - build fantasy cricket teams. The concept seemed simple enough - pick the parameters you want to maximise on, and implement the algorithm. 

Implementing seemed like a bitch. The NSGA-II algorithm was an extremely computation-intensive algorithm that involved many iterations, so I knew I couldn't write the algorithm from scratch and expect to get an optimized implementation. I had either go for Python genetic programming libraries, or find someone else's implementation of the algorithm. I checked out [Deap](https://code.google.com/p/deap/) - it looked like it could effectively give me what I needed. But setting up was really hard. I couldn't make much progress even after hours of reading the docs. So, Deap is on hold. 

I found [another implementation of NSGA-II](https://code.google.com/p/pynsga2/) that used multiprocessing to improve the speed of implementation. It required the fitness to be in a separate file - I need to try it out and see how that works.

So for now, it's still an experimentation phase with the implementation of the algorithm. I took some time out to decide the parameters I'd want to maximise the fitness on. 

BATSMEN :

* Runs per wicket : The batting average of the batsman. For good batsmen in the current cricketing world, this number hovers around 40. 

* Runs per 100 balls : The strike rate of the batsman. A strike rate of >85 is generally considered very good. A batsman with a 100+ strike rate is an ideal pinch hitter to finish the innings.  

* Pinch hitting rate : Boundaries scored per 100 balls, with more weight given to sixes. So effectively,
```python
pinch_hitting = 100.0 * (fours + (1.5 * sixes)) / balls_faced
```

BOWLERS :

The standard bowling statistics require to be minimized on. So for convenience sake, I took the inverse of these numbers, so I could maximise on them.

* Overs to concede 100 runs : A number built from the inverse of the economy rate. For good bowlers, this number is somewhere in the mid-20s. 

* Wickets per 10 overs : Built from the inverse of the bowling average. It is usually >1.5 for good strike bowlers. 

* Overs to concede 10 boundaries : Built from the inverse of the bowler's pinch hitting conceding rate, with weightage for sixes. 

The hard part is finding ways to measure fielding/wicketkeeping performance. It was possible to find the total number of field dismissals that a player, but there's no way to know how many matches the player played. I only have the number of innings he batted or bowled in. It is possible that he played a match where he didn't bat, didn't bowl and didn't have a catch or run out credited to him. 

I need a way to quantify a player's field performance. And I need to see how to implement NSGA-II to draft my team.

Updates soon.
