Final Project: Analyzing Hate Speech
For this project we will suppose the author is a data scientist working on behalf of a Vietnamese government stakeholder interested in curtailing online harassment. Follow along as we walk through the process of defining and isolating hate speech

Table of Contents
1. Business Background
2. Data Understanding
3. Data Cleaning
4. Preprocessing Data
5. First Simple Model (linear regression)
6. Baseline Model (logistic regression)
7. Second Model (naive Bayes)
8. Conclusion
9. Reccomendation
10. Sources

Business Background
The earliest use for what would eventualy become the internet was for the exchange of text and other messages. For nearly as long, a major problem in any virtual forum has been those who would rather harass and intimidate than communicate. As society and culture have been thrust more and more into these online public centers, the salience of this issue has only grown for stakeholders including the owners and operators of these public forums and the infastructure behind them, from the individual user to the highest levels of government. We aim to use the tools of analysis at our disposal to further define efforts agaisnt this maladaptive social behavior.

Data Understanding
Our data for this inquiry is generosly provided by the Vietnamese and international researchers who have scraped the major social media platforms (everything from YouTube to TicTok to Facebook to Twitter) who meticulously curated approximately 30000 comments, sorting them as either clean, offensive, or hateful. A subset of that data was put to use for our purpose here.

Datasets provided by source material : @InProceedings{10.1007/978-3-030-79457-6_35, author="Luu, Son T. and Nguyen, Kiet Van and Nguyen, Ngan Luu-Thuy", editor="Fujita, Hamido and Selamat, Ali and Lin, Jerry Chun-Wei and Ali, Moonis", title="A Large-Scale Dataset for Hate Speech Detection on Vietnamese Social Media Texts", booktitle="Advances and Trends in Artificial Intelligence. Artificial Intelligence Practices", year="2021", publisher="Springer International Publishing", address="Cham", pages="415--426", abstract="In recent years, Vietnam witnesses the mass development of social network users on different social platforms such as Facebook, Youtube, Instagram, and Tiktok. On social media, hate speech has become a critical problem for social network users. To solve this problem, we introduce the ViHSD - a human-annotated dataset for automatically detecting hate speech on the social network. This dataset contains over 30,000 comments, each comment in the dataset has one of three labels: CLEAN, OFFENSIVE, or HATE. Besides, we introduce the data creation process for annotating and evaluating the quality of the dataset. Finally, we evaluate the dataset by deep learning and transformer models.", isbn="978-3-030-79457-6" }

This data is heavily imbalanced towards 'clean' or inoffensive speech, but relatively balanced between the offensive and hate categories.

![image](https://user-images.githubusercontent.com/122270915/233454994-4bae0c95-cf98-4643-96c0-d1d65aed1cc7.png)


Cleaning Data
First we remove any blank comments, then we convert the column names and we subtract each column by one to convert to boolean.

Preprocessing
Here we are going to further prepare our data for making our models by finding the most common phrases in both the offensive and hateful categories so we can use them to predict the accuracy of the hatefulness status. Next we add a column with the count of instances of these words in a given comment. Due to the lack of automated translation only the first 10 words could be translated and were eliminated as most were consonants. Instead we're working with the 10 most common words following that for the list.

Train Test Split
Although we've been generously given a train and a test by the original researchers, to avoid data leakage we are generating our own here.

First Simple Model
From inear regression we can conclude from this that there is an equal likelihood of the common words apppearing in either the offensive or hateful category.

Baseline Model
Here we use logistic regression to improve upon and further refine our initial linear regression by reducing it to a binary. We can conclude similarly to the above from this that the probability of a difference between hateful and non hateful offensive content is small enough as to be nonexistent.

Second Model
For our final model we are using a naive bayes model. Here we will set up baseline probabilities after creating separate lists of our data from both the offensive and hateful categories. Then we'll graph the distributions of the commonly contained words. We'll do another train test split separate from the previous one, then we add our priors. Moving forward we calculate likelihoods using the standard deviation and means. For our purposes we generate a hypothetical new entry into the dataset. Because we are using the boolean true or false status of weather the comment is hateful we only need to define the liklihood for a true value.

Model Comparison
Overall our models returned extremely simlar results showing a negligible differnece between offensive speech and hate speech from the perspective of the measures undertaken here. As of this writing, the error due to the Vietnamese character read in detailed above makes exact valuation impossible until that is resolved.

Reccommendations
With the above information, we can see that there is often little to distinguish offensive speech and hate speech. The strong correlation between offense and hatefulness would suggest offensive speech could be a precursor to hate speech. As such, systems administrators in either the public or private sector could benefit from flagging all sources of offensive tagged speech as potentially hateful and monitor the accounts making them more closely.

Sources
Original Study: https://github.com/sonlam1102/vihsd.git

Vietnamese Consonants https://www.vietnamesepod101.com/lesson/pronunciation-1-the-pronunciation-of-consonants-in-vietnamese/
