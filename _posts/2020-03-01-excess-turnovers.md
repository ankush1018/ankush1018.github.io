---
layout: post
title: "NBA: Understanding Excessive Turnovers"
tags:
  - NBA
hero: /content/2020-03-01-excess-turnovers/cp3.jpg
overlay: blue
published: true

---
![regression results](/content/2020-03-01-excess-turnovers/regression_results.png) 
Many sports blogs and sports broadcasters tend to focus on the number of turnovers (TOV) per game. This can be a useful stat, but it does come with its own flaws. Players who pass the ball a lot (ex. Luka Doncic) or players heavily used on offense (ex James Harden) should be *allowed* to have more turnovers because of how much they do. 

Stats like AST / TOV ratio or USG % / TOV ratio try to do this, but they don't give a wholistic picture. Ideally, we'd use a combination of both (assists and usage rate) to understand the tunrovers a player geneates. 

To understand how TOV-prone an NBA player really is, we want to look at a playes TOV On-Off Difference, also know their TOV plus-minus. This stat can be understood as "when this player is on the court, how many additional TOV does he cause ". However, the main issue is with this On-Off stats are [inherently noisey](http://www.basketballinsiders.com/the-virtues-of-plus-minus-statistics/)

**My goal is to explain TOV On-Off in a less noisey way.** I want to explain TOV On-Off with easily measurable stats such as an idividual players turnovers (TOV), assists (AST), and shots taken (FGA and FTA). To do this, I will use a multivariate linear least squares regression. The result will a stat **XTOV** that better identifies which players create excess turnovers for their team. 

## Regression Characterstics

* TOV_On_Off ~ AST + TOV + FGA + FTA
* Player must have played at least 1000 minutes
* All stats are per 100 posessions 
* Data comes from 2010 - 2020 regular season data
* Regression is fit with no intercept

## Regresion Results And Interpretation

**XTOV = TOV - .2285 AST - 0.09 FGA -0.07 FTA**

This regression suggests 1 TOV every 4 assist, 11 FGA, or 14 FTA is okay. Players like James Harden, Lebron James, Luka Doncic might have have a lot of TOV, but that's okay given how many assists and shots they take.

## Final Thoughts

* CP3 is truley an amazing point guard! He showed up 5 times out of the top 10 player performances in the entire dataset!

* The XTOV stat suggests that traditional big men like Dwight Howard, Demarcus Cousins, DeAndre Jordan, etc are guilty of creating excess TOV.

* To further improve this regression, we could dig deeper into shot type. For example, turnovers that are the result of high quality shots, such as layups, should be more tolerable than a turnover from a contest mid-range.

## Plots
![Chris Paul](/content/2020-03-01-excess-turnovers/Chris_Paul.png) 
![LeBron_James](/content/2020-03-01-excess-turnovers/LeBron_James.png) 
![James_Harden](/content/2020-03-01-excess-turnovers/James_Harden.png) 
![DeMarcus_Cousins](/content/2020-03-01-excess-turnovers/DeMarcus_Cousins.png) 
![Dwight_Howard](/content/2020-03-01-excess-turnovers/Dwight_Howard.png) 
![Stephen_Curry](/content/2020-03-01-excess-turnovers/Stephen_Curry.png) 
![Giannis_Antetokounmpo](/content/2020-03-01-excess-turnovers/Giannis_Antetokounmpo.png) 
## Kudos:
This analysis was largley influened by the work of my favorite rogue sports bloggers reddit [u/ca1294](https://www.reddit.com/user/ca1294). And thank you to u/swar for the amazing (and thoroughly doucumented) [nba_api package](https://github.com/swar/nba_api)





