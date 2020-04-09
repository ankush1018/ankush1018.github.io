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
When evaluating high turnover players, it is common for many fans to focus on a certain number of turnovers (TOV) per game. This can be a useful stat, but it does come with a few flaws. Players who pass the ball a lot or heavily used on offense (ex. Luka Doncic, James Harden) should be *allowed* to have more turnovers because of how essential they are to their teams’ offenses. 

Stats like *AST / TOV*  or *USG % / TOV* try to do this, but they don't give a wholistic picture. Ideally, we would use a combination of both assists and usage rate to understand the turnovers a player generates. 

To understand how turnover-prone an NBA player really is, we want to look at each players TOV On-Off Difference, also known as their TOV Plus-Minus. This stat can be understood as *"when this player is on the court, how many additional turnovers does cause his team?”* This stat is useful, except that On-Off stats are [very noisy.](http://www.basketballinsiders.com/the-virtues-of-plus-minus-statistics/)

**My goal is to explain TOV On-Off in a less noisy way.** I want to explain TOV On-Off with easily measurable stats such as an individual players turnovers (TOV), assists (AST), and shots taken (FGA and FTA). To do this, I will use a multivariate linear least squares regression. The result will a stat **XTOV** that better identifies which players create excess turnovers for their team. 

## Regression Characteristics

* TOV_On_Off ~ AST + TOV + FGA + FTA
* Player must have played at least 1000 minutes
* All stats are per 100 possessions 
* Data comes from 2010 - 2020 regular season data
* Regression is fit without intercept

## Regression Results And Interpretation

**XTOV = TOV - .2285 AST - 0.09 FGA -0.07 FTA**
This regression suggests 1 TOV every 4 assist, 11 FGA, or 14 FTA is okay. So players like James Harden, Lebron James, Luka Doncic might generate lot of turnovers, but that's okay given how many assists and shots they take.

## Final Thoughts

* CP3 is truly an amazing point guard! He showed up 5 times out of the top 10 player performances in the entire dataset!

* The XTOV stat suggests that traditional big men like Dwight Howard, Demarcus Cousins, DeAndre Jordan, etc are guilty of creating excess TOV. This is interesting because he low-post and paint tend to be high turnover zones

* To further improve this regression, we could dig deeper into shot type. For example, turnovers resulting of high-quality shots, such as open. layups, are more acceptable than turnovers from a contested-midrange. 

## Plots
![Chris Paul](/content/2020-03-01-excess-turnovers/Chris Paul.png) 
![LeBron_James](/content/2020-03-01-excess-turnovers/LeBron James.png) 
![James_Harden](/content/2020-03-01-excess-turnovers/James Harden.png) 
![DeMarcus_Cousins](/content/2020-03-01-excess-turnovers/DeMarcus Cousins.png) 
![Dwight_Howard](/content/2020-03-01-excess-turnovers/Dwight Howard.png) 
![Stephen_Curry](/content/2020-03-01-excess-turnovers/Stephen Curry.png) 
![Giannis_Antetokounmpo](/content/2020-03-01-excess-turnovers/Giannis Antetokounmpo.png) 
## Kudos:
This analysis was inspired by my favorite sports blogger [u/ca1294](https://www.reddit.com/user/ca1294). Also, thank you to u/swar for the amazing (and thoroughly documented!) [nba_api package](https://github.com/swar/nba_api)





