---
layout: post
title:  "Project: ⚽ World Cup 2018 Prediction"
date:   2021-11-01 16:30:58 +0100
categories: jekyll update
---
# Project Overview 
* End to end project researching the effects certain attributes have on the value of a car
* Optimized Linear Regression model using only relevant data in a date range

[View Code](https://github.com/MattithyahuData/P1-World-Cup-2018-Prediction/blob/main/Code/P1_Code.ipynb)

## Resources Used
**Python 3** 

[**Anaconda Packages:**]((https://github.com/MattithyahuData/P1-World-Cup-2018-Prediction/blob/main/requirements.txt) **pandas, numpy, scikit-learn**

Kaggle Data source links: 
* [results](https://www.kaggle.com/martj42/international-football-results-from-1872-to-2017/data?select=results.csv) 
* [fifa_rankings](https://www.kaggle.com/tadhgfitzgerald/fifa-international-soccer-mens-ranking-1993now) 
* [fixtures](https://fixturedownload.com/feed/json/fifa-world-cup-2018)

## Data Collection
Download Sources: Kaggle | fixturedownload
* Using all international game data was key, as we needed past instances of teams performances
* Here I downloaded the data sources from Kaggle as a csv
* I used the read_json function to read the fixtures data into python

## Data processes
Mainly an optimisation project to see if shortening the years of data used would maybe improve the model performance.

## Evaluation 
Based on the actual results the model did not perform well, in future collecting better quality data would help with the quality of the model and the prediction. 
Also, not every think requires machine learning! Know when to and when not to use it. 

## Conclusions
* Filtering out irrelevant historic match data

The highest level of football before Senior football is U21 football. For national teams the AVG squad age is between 24 - 29.6 years. Players under the age of 21 rarely get recruited to the senior team so to accommodate for those that may be 21 years old will be our lower bound. To accommodate for older players our upper bound will be 30 years. 

* It is rare for teams to stay together for longer than 5 years in any sport, some people get better in their game and stay others get worse and are dropped, some retire, some leave through injury. The list is endless, based on this number I will only collect data from up to 5 years before the day before the first game of the World Cup

* Because we want a clear view of the performance of the current squad and not the England team of 1966 for example because that isn’t the team playing now. A limit of 9 years would help improve this bias.  
* Currently doing more research to validate any lower or higher number. I will simply update the function input when I get this info. 
* Past performance of previous squads does not guarantee future performance 

## Project Management (Agile | Scrum)
* Resources used
    * Jira
    * Confluence
    * Trello 

## Questions | Contact me 
For questions, feedback, and contribution requests contact me
* ### [Click here to email me](mailto:contactmattithyahu@gmail.com) 
* ### [See more projects here](https://mattithyahudata.github.io/) 


[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
