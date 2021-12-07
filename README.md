# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 3: Web APIs & NLP

### Problem Statement ###

In this project we will scrape data from `r/LifeProTips` and `r/YouShouldKnow`. These subreddits both contain similar posts which are typically useful factoids in nature. The posts are also generally random and very varied in terms of information provided. We will attempt to generate NLP models to sort the posts into their respective categories. We will share these findings with our fellow data scientists for peer review.

---

### Methodology

The project consists of 3 main parts and a presentation:
    1) Utilize an API for data acquisition and then proceed to clean and pre-process the data for modelling
        2) Generate baseline model and other models for comparison. Here we also decide on whether we proceed or drop models
        3) Evaluate the chosen models based on accuracy, recall, specificity and feature importances
        4) Presentation of our findings to fellow data scientists

---

#### About the Pushshift's API

We used <a href="https://github.com/pushshift/api">Pushshift's API</a> to assist in our data acquisition.

For more information on the API, please see video on how to use: https://youtu.be/AcrjEWsMi_E

**NOTE:** Pushshift is now limited to 100 posts per request (no longer the 500 in the screencast).

---

### Executive Summary

Overall the project was a difficult one. With similar contents both coming from `LifeProTips` and `YouShouldKnow`, we were only able to generate a model that peaks at 80% accuracy.

Among the models, we can conclude that the stacking classifier model performs the best with the highest accuracy. Recall and Specificity are also the highest among the models (except logistics regression recall score) and are relatively balanced. Recall score is 82%, while specificity is 79%.

Second to this model is actually the tuned Random Forest model at an accuracy score of 79%. Recall and specificity are 85% and 72% respectively. This makes it the best model at predicting `LifeProTips`, even against the stacking classifier.

Unfortunately I was unable to decode the entirety of the stacked model during the duration of the project, but that is an area of future studies.

---

### Data Dictionary

| Syntax      | Description                                                  |
| ----------- | ------------------------------------------------------------ |
| subreddit   | target classification classes. For modelling, LifeProTips = 1, YouShouldKnow = 0 |
| id          | unique id of posts to avoid duplicates                       |
| title       | Title of posts                                               |
| selftext    | content of posts                                             |
| created_utc | time the post is created                                     |
| text        | composite of text and self text; processed to be our feature for modelling |

---

### Future Recommendations

For future recommendations, two steps could be taken. Firstly is to try other types of models and see if they can fit better. Secondly is to tune the parameters of our best model. With more resources, we could include different vectorization methods, run a gridsearch on the vectorizing transform on top of the modelling, or even perform a stacked model on these pipelines.

