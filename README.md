# NLP on Amazon Reviews to Aid Customer’s Decision Process

## Abstract
A 150 word description of the project idea, goals, dataset used. What story you would like to tell and why? What's the motivation behind your project?

Popular Amazon products usually have thousands of reviews from various users explaining the pros/cons of the products along with a description of their personal opinion on the product. While this data may be useful to Amazon customers, often times these comments are time-consuming to sift through. Additionally, users may get more confused reading many positive and negative reviews and Amazon may lose a potential customer. In order to save users time when they are online shopping, we want to conduct a keyword analysis on these reviews by identifying positive and negative words to help a user quickly determine whether they may want this product. After summarizing, we plan on  creating a visualization for these reviews. The dataset used for this study comes from UCSD Julian McAuleys “Amazon product data” dataset.

## Research questions
A list of research questions you would like to address during the project. 

* Can we generate keywords from Amazon reviews through sentiment analysis?
* Can we use sentiment analysis to improve similar word search?

## Dataset
List the dataset(s) you want to use, and some ideas on how do you expect to get, manage, process and enrich it/them. Show us you've read the docs and some examples, and you've a clear idea on what to expect. Discuss data size and format if relevant.

List the dataset(s) you want to use, and some ideas on how do you expect to get, manage, process and enrich it/them. Show us you've read the docs and some examples, and you've a clear idea on what to expect. Discuss data size and format if relevant.

We would like to use the Amazon reviews dataset provided to us. We will be using the 5-core (9.9gb) subset of the data where the items/users have at least 5 reviews. The dataset contains 41.13 million reviews and filters out both users with multiple accounts and plagiarized reviews. 

Each JSON object contains the following data: reviewerID, asin, reviewerName, helpfulness, reviewText, overall, summary, unixReviewTime, and reviewTime

Here is an example below: 
![picture alt](https://github.com/sdhar3/ADA-Project/blob/master/example.png "example of one review")

Our intention is to conduct sentiment analysis on the data and the Amazon product data website recommends we use this data set specifically. 

We are going to take the review text from the file and the “overall” from each comment and anything above a “overall” of 3 will be labeled as positive and anything below will be labeled as negative. Then we will create a deep neural network to conduct sentiment analysis. We are going to run a couple noise reducing algorithms to clean up filler words and create higher accuracy within analysis. 

We also plan to do data visualization to see how related certain words are to each other. 

## A list of internal milestones up until project milestone 2
Add here a sketch of your planning for the next project milestone.

Tasks before November 11th:
* Clean the data and combine the datasets
* Run noise reduction methods remove filler words and improve the speed of the deep network

Tasks before November 18th:
* Write the code for the deep neural network create graph showing what words are indicative of positive review and what words are indicative of negative reviews.
* Look at graphs and create a method to find similar words.

Tasks before November 25th:
* Apply the model to find keywords for the reviews so that it become easier for future customers to get a better general idea of the reviews without have to read all of them.
* Visualize these keywords for some of the reviews that were given for particular items being sold on Amazon.

## For Milestone 2 
We pivoted our idea towards predicting the helpfulness of a review based on just the words in a review. So far, we have tried 2 seperate models. The first being a model built with keras. This basis for the model is to take the reviews and extract to the vocabulary in the reviews to then predict the helpfulness. The second model we tried was a neural network that we built from scratch. The model is a single layer model for which you can change the number of hidden nodes in the hidden layer. The neural network that we built is faster because it removes some ineffiencies in math for the back prop and forward pass when updating the weights between layers. This model also use a ratio to express what words appear more in helpful reviews and which words appear more in unhelpful reviews. The results from both models are not so promising as they only perform, on average, 5%-10% better than random guessing. We have tried many different ways to try to get better results including the following:
* creating a helpfulness factor that accounts for a higher number of good reviews.
* changing the number of hidden nodes, learning rate, min_count for removing highly specific words, and polarity_cutoff.
* adding more data from different datasets
* changing the training size to testing size ratio

For next steps we are going to try another type of neural network, and add more steps to the pre_processing for words.

Some patterns that I have began to see:
* It is my belief that the datasets are to broad. I think that if we run the model on data from specfically jean reviews or phone reviews, that we would get much better results. This is because from looking at the words that are appear more often in helpful reviews, we see that they are more specfic. My thoughts on this are that the categories right now are too generic and for reviews to be considered helpful they need to be, in general more specific. Reviews that just say something along the lines of "this is great!" will not get higher helpful reviews, but more in detail reviews will. Therefore the word specificity is very important and the categories need to be smaller because generic words do not hold much value with regards to helpfulness. The next step is to see if can filter these categories a little more.
* The models are basically sentiment analysis if the min_count is increased and the polarity =0.
* I will add one more layer to the neural network to see if that helps.

## Questions for TAa
Add here some questions you have for us, in general or project-specific.

## For Milestone 3 
Shikhar: Did the intial preprocessing of the data. Helped in the process of determining which models to use. Helped in writing the report.</br>
Shruti: Helped in the process of determining which models to use. Worked on further optimization of code after the intial model. Helped in writing the report.</br>
Varun: Helped in the process of determining which models to use. Worked on coding the model and obtaining the results. Helped in writing the report.
