# Sentiment Analysis

## The Project
I completed the following project as part of the NLP (Natural Language Processing) module for final-year undergraduates studying Computer Science at the University of Bath. An overview of the detailed report is presented below.

Sentiment analysis is the process of analyzing text to determine its emotional tone (positive or negative). In this project, we explore a typical pipeline for a machine learning project, particularly an NLP one, by examining three models for sentiment analysis: Naive Bayes, Logistic Regression, and Support Vector Machines. Specifically, we investigate the effectiveness of each model in classifying the tone of a movie review (positive vs negative), with each model trained and tested using the Large Movie Review Dataset provided by Stanford. This dataset contains thousands of movie reviews collected from IMDb. We experiment with the different hyperparameters possible for each model, as finally test the best models found on the test set to compare final performance. 

The SentimentAnalysis.ipynb provides the code used to test these different models, as well as a personal implementation of the Naive Bayes model from scratch. The report gives a more detailed overview of the general pipeline, which includes the following steps involved in developing an NLP application:
1) Input, clean, pre-process, and split data into training, development, and test sets (e.g., storing text data and corresponding labels in separate lists, tokenizing, lemmatization, use).
2) Inspect training data and extract features (e.g. are just words useful in determining tone, how about looking for certain phrases?)
3) Train and evaluate your chosen model on the development set, iterating by examining results and deciding if adjustments are needed (given that this is an exploratory project, we know going in that we are going to experiment with different models to investigate accurcacy)
4) When satisfied with performance on the development set, evaluate the model on the test set and report performance.

The below also outlines a general pipeline for developing an ml application, as followed in this project, guided by [Ekaterina Kochmar's lecture notes ](https://ekochmar.github.io/nlp-course/):
![GeneralMLPipeline](https://github.com/user-attachments/assets/c2616dae-f20b-4cb2-944f-7e9bba825505)

## Exploring N-Grams
My exploration specifically focused on the use of N-Grams in Sentiment Analysis. Quoting MathWorks
> 'An n-gram is a collection of n successive items in a text document that may include words, numbers, symbols, and punctuation.'

For instance, a unigram refers to the use of single words in a text. Not thinking about stop-word removal for a second, etc, the idea is that a classifier using only unigrams to clasify sentiment would view the text "I love this movie" as "I", "Love", "This", "Movie". If we are also considering bigrams, then the model would also taken in as data "I love", "love this" "this movie". The idea is that unigrams alone may not fully capture this sentiment.
> Consider "The movie was not good.' Considering the words as individual units means we would receive "not" and "good" and not understand how these relate to each other. "good" may connote positive sentiment, but "not" will probably convey negativity. However, using bigrams we would be able to capture "not good" as a phrase, and clearly see this as an overall negative tone.

The above gets interesting very quickly. Looking at text data how would you classify the following: "A masterpiece! I really loved how the plot did not move forward at all, I loved losing two hours of my life." This is clearly negative, but what if we look at the words as units, we see 'masterpiece' and 'loved', and so may conclude this as positive. This quickly shows how such tasks become interesting for models to solve. Increased n-grams may help the above, but we may want to turn to other approaches in such problems, such as transformers. Although a slight tangent, this is still fun to think about. Here, however, we focus on use of n-grams. 

## Results
Before we look at the final results, we can briefly note the following:
1) I initially focused on training and testing each model using the training and development sets, experimenting with different hyperparameters for each model. For instance, I inspected the SVM classifier with six different combinations of hyperparameters to determine which combination performed best among all tested combinations. This model was then selected as the SVM model for evaluation on the test set. So, 'hyperparameter combination' refers to a specific set of hyperparameters tested during the training and evaluation of the SVM models, which is detailed in the report for those interested in the specific values, as well as a description on what these hyperparameters are doing.

2) In general, all feature sets used for training were TF-IDF matrices generated after the movie reviews had been tokenized and lemmatized. The difference, then, lies solely in the number of n-grams used to examine how n-grams affect performance. As we will see, considering bigrams also improved the performance of both the Naive Bayes and Logistic Regression classifiers.

The results from each model's best classifier on the test set is shown below.
  
<img width="1247" alt="Screenshot 2024-10-17 at 10 44 14" src="https://github.com/user-attachments/assets/ad641e6a-1bb4-478d-8046-4371434c1e2b">

## Conclusion & Future Work
The best model appeared to be the Logistic Regression model, which achieved an accuracy of 87%, showing a clear improvement over the Naive Bayes model. To get a better idea of how well the model is doing, we need evaluate these results in terms of a baseline, such as human performance.

>  This source ([1]) states that, when evaluating sentiment in a piece of text—specifically dealing with three sentiments (positive, negative, neutral)—human analysts tend to agree approximately 80-85% of the time.

The fact that these relatively simple models achieved an accuracy that meets or exceeds this baseline is noteworthy. It would be interesting to explore how more advanced models, such as BERT, could further improve this performance.


## Technologies
<p>
  <img alt="Python" src="https://img.shields.io/badge/Python-ffffc5?logo=python&logoColor=black"/>
  <img alt="Scikit-Learn" src="https://img.shields.io/badge/Scikit--Learn-ffdbbb?logo=scikitlearn&logoColor=black"/>
  <img alt="NumPy" src="https://img.shields.io/badge/NumPy-add8e6?logo=numpy&logoColor=black"/>
</p>

[1]: https://www.lexalytics.com/blog/sentiment-accuracy-baseline-testing/#:~:text=Setting%20a%20baseline%20sentiment%20accuracy,training%20a%20sentiment%20scoring%20system.



