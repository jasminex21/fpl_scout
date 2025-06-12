# FPL Scout

### Proposal 
I intend for this to be an in-depth analysis of machine learning techniques in optimizing Fantasy Premier League (FPL) lineups. This is something I have explored in the past to limited success and applicability ([repo](https://github.com/jasminex21/FPL_predictions)). Football, and sports in general, is often unpredictable. However, evidence-based and explainable predictions can still be concluded from the wealth of sports data available. 

My ultimate aim is to be able to optimize my performance in FPL. For those unfamiliar, FPL is a fantasy football (soccer) game where you are given limited funds to select a lineup of Premier League players who you believe will give you the highest point haul. Players earn points by scoring goals, assisting, and via position-specific achievements (e.g., clean sheets for defenders, goalkeepers, and midfielders). You can alter your team each gameweek by choosing a captain (whose points are doubled), deciding which players to bench, and transfering in new players (you get one free transfer per week; additional transfers cost 4 points each).

Hence, the total points you earn each week largely comes down to: 

1. The choice of captain - choosing to captain a player who scores 15pts (30 if C) vs a player who scores 2pts (4 if C) clearly makes a huge difference. 
2. The choice of players to bench vs players in the starting XI. 
3. Based on underperforming players or positions in the squad, the choice of players to transfer in. Which transfers would make the largest impact on the squad, while taking into consideration available team funds?

Some approaches: 

* Ranking the players in the squad by their predicted number of points. The player ranking first would be the ideal choice for captain (and naturally, the player ranked second would be vice captain). If a player ranks last or around there consistently and consecutively, they would probably be top choices to transfer out. Based on that, reasonably-priced replacement players who perform better can be highlighted from the remaining dataset.

Data sources: 
* The FPL API, for each gameweek and each player, mainly provides data specific to FPL itself, i.e., points scored, transfers in/out, etc. It also has some broad features such as "influence," "creativity," etc. For my past investigation, I used the FPL API as my sole source of data, which hindered prediction accuracy and effectiveness because of the lack of specificity in my data, as well as circumstances that were lacking, such as injury statuses, suspensions, and opponent difficulty. 
  * This time, I intend to pull data from other sources, such as FBREF, that will allow me to take into account a greater breadth of factors contributing to a player's game success. 

Questions to answer: 

* How do I determine a player's form? In the past, I used rolling statistics - i.e., how well a player performed in the past 3 games. A similar approach can be taken here, but perhaps using a better selection of metrics. Also, a baseline should be established for each player as well; some players are simply better than others, and also, this would be useful when it comes to recommending lineups at the beginning of the season when rolling statistics cannot be computed. 
* What features should be used in making predictions? I want to note that in the past, I had one model that made predictions for every player regardless of position. I'm thinking that this time around, it may make more sense to construct a model for each position.
* How do I obtain the most up-to-date data? FPL players should update their squad each gameweek, and so predictions must be made at least every gameweek. Circumstances change day-to-day in the world of sports as well - e.g., if an injury occurs after a prediction is made, that should be reflected. 