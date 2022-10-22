## Men's World Cup 2022 - Simulation
#### Dataset from: https://www.kaggle.com/datasets/cashncarry/fifaworldranking

Here I run a simulation based on the ranking of all teams to draw the probabilities of the different teams winning the Men's World Cup. I calculated the probability to win the championship and how likely all teams are to get to the different phases of the World Cup.

Summary of results:

1) The Top 4 countries with more chance of wining the World Cup are:
    
    i) Brazil 19%
    
    ii) Belgium 16%
    
    iii) Argentina 10%
    
    iv) France 9%

2) The most likely Final is Brazil vs Belgium 6%

3) The Poisson stochastic model for goals can predict the FIFA formula for the expected outcome of a match.

4) There is a correlation between the initial Elo Rank and the outcome of the tournament. This means that the random placement of the teams didn't change much the odds of each team to win. This can be predicted by a simple 'Mean-Field' model using the match expected outcome formula from the FIFA Elo rating. At each round, the probability to advance is given by the outcome probability with respect to an 'average team', where each round the strenght of this 'average team' increases by the Half-normal distribution.

#### Limitations of the simulation:

The central part of the simulation is the method to predict the outcome of the match. The number of goals scored by each team is given by a Poisson process where the average number of goals is modelled by [see Ref. 1]:
$$\mu = e^{\alpha_0 + \alpha_1 \Delta Elo/400}$$
Here the constants $\alpha_0, \alpha_1$ were copied from Ref. 1 and compared to the expected formula for the match outcome used by FIFA [see Ref. 2,3,4]. I haven't implemented a linear model to calculate these constants.

Another important limitation of my model are the group tiebreaks where I haven't considered all the different levels one can have a tie. I only considered the ranking by number of points, net goals and total goals by the teams. This can cause small differences but I don't expect these to affect the results substantially.

The final aspect that I haven't implemented are the odds for penalties of every team. After the group stage, if the match is a draw the teams have a penalty shoot-out. Here I considered that the teams have probabilities to win the penalties proportional to their Elo's. I haven't checked if that is true historically so I suspect that might change the results slightly.

#### References:
1) https://eightyfivepoints.blogspot.com/2018/05/what-can-we-expect-from-21st-fifa-world.html

2) https://www.eloratings.net/

3) https://en.wikipedia.org/wiki/World_Football_Elo_Ratings

4) https://www.fifa.com/fifa-world-ranking/men?dateId=id13603
