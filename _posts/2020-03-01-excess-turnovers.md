---
layout: post
title: "Evaluating High Turnover NBA Players"
subtitle: "Smarter Way To Identify High Turnover Players"
tags:
  - NBA
hero: /content/2020-03-01-excess_turnovers/regression_results.png
overlay: blue
published: true

---

![regression results](/content/2020-03-01-excess-turnovers/regression_results.png)

# Background
As the NBA evolves and competition increases, teams are getting even more creative to seek any possible edge, with the ultimate goal of holding the championship trophy in June. In the final minutes of a playoff game, NBA teams require their top lineup to consist of elite shooting, defending, rebounding, passing, and minimal turnovers. 

Many sports blogs and sports broadcasters tend to focus on number of TOV per game. This can be a useful stat, but it can not come without its flaws. Players who pass the ball a lot (ex. Luka Doncic) or players heavily used on offense (ex James Harden) should be allowed to have more turnovers because of how much they do. Stats like AST / TO ratio or USG % / TO ratio try to do this, but they don't give a wholistic picture Ideally, we'd use a combination of both (AST and Usage / shots taken) to explain the turnovers a player generates. 

Rather than looking at a players number of turnovers per game, we care more about "when this player is on the court, does the player cause his team to turn the ball over more?" In other words, does this player create an excess number of turnovers after considnering their impact on the game? TOV On-Off Differential is a great stat that answers this question. The main issue is that On-Off stats are [inherently noisey](http://www.basketballinsiders.com/the-virtues-of-plus-minus-statistics/)

My goal is to examine the relationship between excess turnovers by a player(Team TOV On Off Diff) vs that players indivual assist, turnovers, free throw attempts, and field goal attempts. To do this, I will use a multivaraite oridnary least squares regression. 

# Regression Characterstics

* TOV_On_Off ~ ASST + TOV + FGA + FTA

* Player must have played at least 1000 minutes

* Data from 2010 season onwards and only regular season data

* Regression fit without an interncept 


## Regresion Results After Rescaling and Simplying 

Team TOV Diff = TOV - .2285 AST - 0.09*FGA -0.07*FTA

This regression suggests 1 TOV every 4 assist, 11 FGA, or 14 FTA is okay. Players like James Harden, Lebron James, Luka Doncic who pass and shoot a lot are 'allowed' more TOV before it gets excessive. 

# Final Thoughts And Plots:
* CP3 is truley an amazing point guard! He showed up 5 times out of the top 10 player performances in the entire dataset. 
* Big Men like Dwight Howard, Demarcus Cousins, DeAndre Jordan and many more are guilty of creating excessive TOV. I believe this is largley influenced by the paint being a high turover zone.
** That being said, in the 2019-2020 season (before the season was suspened), Nikola Vucevic as a center is a top 3 player in generating the fewest excess turnovers.
* Just because a player commits high number of turnovers doens't mean that player is creating 'excess turnovers'


# Kudos:
This analysis was largley influened by the work of my favorite rogue sports bloggers reddit [u/ca1294](https://www.reddit.com/user/ca1294). I strongly encourage you to check out his posts on Reddit! 
And thank you to swars for the amazing pacakge NBAPy to pull the results!

