## Introduction
The subject of my internship in the quality department of Thales was to predict the arrival of potential future problems that could arise within the different projects carried out by the different entities of the company. The projects are monitored by different quality engineers who regularly write a quality report evaluating different aspects of the project's progress and therefore highlighting any problems encountered. These reports, which are called Quality Advices, are therefore the data that I processed.

### Quality Advices

A QAdvice is made up of 14 topics covering different aspects of a project, from customer relations to respecting the schedule... These different points are evaluated by the quality engineer according to this scale:
<br/>

<p align="center">
  <img src="image/bareme.png"/>
</p>
<p align="center">
  <i>Figure 1. KMA scores scale</i>
</p>

These different points are called Key Maturity Area (KMA) and therefore compose. Each KMA evaluation is accompanied by 2 comments. The first one is a finding comment which is there to justify the grade given by the engineer. It is therefore used to describe a problem. The second one is a recommendation comment which is used to inform the team to evaluate actions or decisions to be implemented to solve the problem. This report is formatted as an excel file like this :
<br/>

<p align="center">
  <img src="image/QAdvice_exemple.png"/>
</p>
<p align="center">
  <i>Figure 2. Presentation of a QAdvice</i>
</p>

 The objective of this project is therefore to try to predict the value of the next KMA scores of the future QAdvice. Thus it will be possible to predict potential problems on some specific points.
 
### The Data

The starting data was simply a .csv file containing more than 2 years of QAdvice from more than 100 projects. It contained the KMA score evaluations, comments and descriptions of the projects in question.
However, the raw data is not directly usable to train a learning machine model. It was therefore necessary to do some pre-processing work. So I decided to transform the date into several columns: the date of the day, the day of the week, the season, the month ...
But with these simple modifications, the first results of the first models were not very satisfactory (about 60% of precisions), so I added metrics allowing the different models to better apprehend the data set. That's why I added statistics on the previous KMA scores of the previous QAdvices.
Another variables that were not exploited were the comments of the KMA scores. For their value data I decided to use a sentiment analyzer from an NLP library(NLTK). Thus, each comment is rated by a score from 1 to 4 transcribing the positivity or negativity of the comment left by the quality engineer. This makes it possible to correlate the KMA score with the engineer's opinion.

Once the data was processed, I was able to train the first relevant models. Here are the results obtained:<br/>
<p align="center">
  <img src="image/resultsML.png"/>
</p>
<p align="center">
  <i>Figure 3. Details of different models of Machine Learning</i>
</p><br/>
The best performing model here is the random forest with almost 88% accuracy. The following are the most important variables in the decisions made by the model:
<p align="center">
  <img src="image/variables.png"/>
</p>
<p align="center">
  <i>Figure 4. Variables determining model predictions</i>
</p><br/>

### Random Forest
