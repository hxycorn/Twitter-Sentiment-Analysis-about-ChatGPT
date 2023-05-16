# Twitter-Sentiment-Analysis-about-ChatGPT
A quantitative study on over 1.25 million tweets about ChatGPT, employed data scrapping, data cleaning, EDA, topic modeling, and sentiment analysis.

<img align="center" src="Image/wordcloud2.png" style="width:400px;height:300px">
<hr>

## TABLE OF CONTENT
- [Background](#background)
- [Objective](#objective)
- [Methodology](#methodology)
  - [Tools](#tools)
  - [Data Collection](#data-collection)
  - [Data Preprocessing](#data-preprocessing)
  - [Data Modeling](#data-modeling)
- [Results](#results)
  - [Exploratory Data Analysis](#eda)
  - [Topic Modeling](#topic-modeling) 
  - [Sentiment Analysis](#sentiment-analysis) 
- [Conclusion](#conclusion)
- [References](#references)

<hr>

## BACKGROUND
ChatGPT is an artificial intelligence chatbot developed by OpenAI and launched in November 2022. It is built on top of OpenAI's GPT-3 family of large language models and has been fine-tuned (an approach to transfer learning) using both supervised and reinforcement learning techniques. Given the advantages of ChatGPT over traditional chatbots, ChatGPT has attracted more than 1 million users in 5 days and 100 million users in 2 months after it was launched, leaving behind other popular online platforms such as Netflix, Facebook, and Instagram in terms of adoption rates. Some early adopters of ChatGPT believe that it will eventually obsolete several professions related to content creation. it has been demonstrated that ChatGPT is capable of producing high-quality responses to a variety of challenges, including solving coding challenges and generating accurate responses to exam queries.

<img align="center" src="Image/user1.png" style="width:300px;height:250px"> <img align="center" src="Image/user2.png" style="width:400px;height:250px">

<hr>

## OBJECTIVE
Using a mixed-method approach, analyze tweets from December 2022 to January 2023 that mention ChatGPT and express diverse and unstructures opinions. Identify the main topics and sentiments of the conversations and examine perception of early ChatGPT users. We assert this identification will allow us to understand and assess ChatGPT's capability, effectiveness, and facing challenges. 

**Research Questions**
- **RQ1** What are the profile characterisitics of ChatGPT early users?
- **RQ2** What are the dominant topics that emerge from the tweets about ChatGPT?
- **RQ3** What are the sentiments that are associated with the tweets about ChatGPT?
<hr>

## METHODOLOGY

### TOOLS
<table style="width:100%">
  <tr>
    <th>Task</th>
    <th>Technique Description</th> 
    <th>Tools/Packages Used</th>
  </tr>
  <tr>
    <td>Data Collection</td>
    <td>Scraping tweets from Twitter </td> 
    <td>snscrape</td>
  </tr>
  <tr>
    <td>Data Preprocessing</td>
    <td>Duplication removal, lowercasing, noise removal (punctuation, stopwords, URLs, @users), lemmatization</td> 
    <td>re, NLTK, pandas, numpy</td>
  </tr>
  <tr>
    <td>Feature Engineering</td>
    <td>Retrieving geographical info from a user's profile location; 
      retrieving datetime info from tweet timestamps </td> 
    <td>geopy, datetime</td>
  </tr>
  <tr>
    <td>Topic Modeling</td>
    <td>Identifying topics using the Latent Dirichlet Allocation (LDA) modelling</td> 
    <td>pyLDAvis, gensim</td>
  </tr>
  <tr>
    <td>Sentiment Analysis</td>
    <td>Quantitative sentiment analysis of each topic via rule-based and deep learning based model</td> 
    <td>VADER, roBERTa, scipy, torch</td>
  </tr>
  <tr>
    <td>Data Visualization</td>
    <td>Multi-attribute plots</td> 
    <td>matplotlib, seaborn, wordcloud, PowerBI</td>
  </tr>
  <tr>
    <td>Environments & Platforms</td>
    <td> </td> 
    <td>Google Colab, Databricks, Pyspark, Jupyter Notebook, Twitter</td>
  </tr>
</table><br>


### DATA-COLLECTION
<table style="width:100%">
  <tr>
    <th>Method</th>
    <th>Notes</th> 
  </tr>
  <tr>
    <td>Tweepy</td>
    <td>3200 tweets; no historical data</td> 
  </tr>
  <tr>
    <td>GetOldTweets3</td>
    <td>Twitter has removed the endpoint the GetOldTweets3 uses </td> 
  </tr>
  <tr>
    <td>Twint</td>
    <td>Twitter throws a more strict device + IP-ban after a certain amount of queries</td> 
  </tr>
  <tr>
    <td><b>snscrape</b></td>
    <td><b>Scrapped 1.25M tweets - 832,924 English tweets</b></td> 
  </tr>
</table>

<h4> Data Collection: Identifying ChatGPT Content </h4>

<li>Package used: snscrape</li>
<li>Language: English</li>
<li>Keywords: ChatGPT</li>
<li>Timeframe: December 1, 2022 to January 31, 2023</li>
<li>Features: User ID, User Name, User Verification, User Location, User Followers, Tweet Text, Posted Timestamp, and Posed Language</li>
<li>Number of tweets collected = 1,255,518</li>
<li>December - 474,572 tweets | January - 780,946 tweets</li>
<hr>

### DATA-PREPROCESSING
<b> Data Cleaning </b> 
- Merged collected datasets into a single dataframe and removed duplicate tweets.
- Dropped 17 tweets that were missing timestamp values.
- Filled missing values in 'Location' column with the term "Unknown". 


**Feature Engineering**
- Utilized the geopy package to obtain the geographic information (specifically, the country) from the profile location associated with each user..
- Extracted both the date posted and the week from the timestamp by means of the datetime package, subsequently discarding the timestamp column.


**English Tweet Text Preprocessing**
- Filtered English-tweets and saved them to a new dataframe.
- Converted all tweets that represented the same word in different cases (e.g. ChatGPT and CHATGPT) to the same lowercase form (e.g.chatgpt).
- Removed noise such as punctuation, URLs, Twitter handles using the "re" library.
- Removed stopwords using the NLTK English stopwords list, and eliminated tokens that were too short (less than three characters) or too long (over 50 characters). 
- Exracted frequently occurring continuous sequence of 2 words (bigram) and 3 words (trigram) within the corpus.
- Performed WordNet-based lemmatization using the NLTK pacakge to transform each word into its base or dictionary form. 


### DATA-MODELING
**Unsupervised LDA**

The unsupervised Latent Dirichlet Allocation (LDA) modelling technique was applied to extract a set of key ChatGPT topics from the collected tweets. 
- Generated a dictionary and corpus containing all the tweet texts, filtering out extreme words with low/high appearing frequency of occurence (occuring in less than 10 tweets or more than 50% of tweets).
- Inplemented LDA using the LdaMulticore module in Gensim library. 
- Conducted a series of experiment by varing the number of topics (N) from 2 to 40, and obtained a relatively high coherence score for the range of 10 to 18 topics. 
- Executed LDA with N=10 and identified 10 topics based on the highly relevant tweets for each topic. 

**Sentiment Analysis**

Sentiment analysis is an approach to identifying the emotional tone behind textual data. Various algorithms (models) are available for sentiment analysis tasks, and each has its pros and cons, such as: 

- **Rule-based (lexicon-based):** Such kinds of models have their own dictionaries (lexicons) of words or emojis with positive or negative weights. These algorithms count the number of positive and negative words in the given text. If the number of positives is more than the negatives, they return a positive sentiment. If both are equal, they return a neutral sentiment. Rules or dictionaries of words can be customized. And these kinds of algorithms do not require any model training.
- **Supervised Machine learning:** These algorithms are fed with many labeled text data until they can learn patterns or the essence of the statement instead of clearly defined rules. However, for this approach labeled data is required, which is not available in our study. 
- **Unsupervised Deep Learning:** Such kinds of algorithms are able to learn patterns through multiple layers from unstructured and unlabeled data to perform sentiment analysis using various learning mechanisms, e.g. self-attention.

In this study, we used both VADER (rule-based model) from the NLTK library and Twitter-roBERTa (deep learning based)from the TRANSFORMERS package to examine the early users' attitude towards ChatGPT.

<hr>

## RESULTS
### EDA
**Tweets about ChatGPT over time**

<img src="Image/tweets_months.png" style="width:400px;height:300px"><img src="Image/tweents_week.png" style="width:400px;height:300px">

- When ChatGPT was first released, there were approximately 250,000 tweets discussing it in the first two weeks leading up to December 11, 2022.
- The number of tweets mentioning ChatGPT in January 2023 was 1.65 times higher than the number of tweets in December 2022.
- In week 9 (1/21/2023-1/29/2023), the number of tweets related to ChatGPT reached its highest point in the past two monts (246,657). 

**Users' Features**

- Verification Status
  - ChatGPT has been adopted by both verified and non-verified users on Twitter: Only 3.1% of ChatGPT users on Twitter are verified.
<img src="Image/verification.png" style="width:350px;height:300px">

- Followers
  - Some high-profile Twitter users with millions of followers have expressed interest in ChatGPT, including Elon Musk, CNN, NYTimes, and others.
<img src="Image/followers2.png" style="width:400px;height:300px">

- Tweeting Frequency
  - From December 2022 to January 2023, a total of 550,655 Twitter users tweeted about ChatGPT.
  - Among these users, 63.42% tweeted only once, while 36.58% tweeted more than once.
<img src="Image/tweets_frequency.png" style="width:800px;height:300px">

- Countries
  - 31.7% users tweeting about ChatGPT were from the United Stats.
  - The top 5 countries where ChatGPT was discussed the most were United States, the United Kingdom, India, Japan, and France.
  - ChatGPT has grabbed attention from users in over 150 countries worldwide.
<img src="Image/country.png" style="width:800px;height:350px">

- Languages
  - Over 70% of users discussing ChatGPT were English speakers.
  - Around 30% of tweets about ChatGPT were written in other languages, i.e. Japanese, Spanish, French, etc., indicating that ChatGPT is also functional in languages other than Engligh.

<img src="Image/language.png" style="width:550px;height:500px">
<hr>

### TOPIC-MODELING
**Optimal Number of Topics and Iterations**

After evaluating coherence score, comprehensibility of top keywords, and computational cost, the study determined the optimal number of topics (10) and iterations (60) for LDA analysis. 

<img src="Image/topicnumber.png" style="width:450px;height:300px"> <img src="Image/iteration.png" style="width:400px;height:300px">

<img src="Image/pyLDAvis.png" style="width:800px;height:500px">

**Topics**

Through a meticulous analysis of the top 20 keywords and hundreds of highly correlated tweets for each topic within the LDA topic modeling results, the study determined a descriptive and meaningful name for each topic. 
The top 3 most discussed topics are:
- T8 Impacts on Work and Efficiency
- T5 ChatGTP's Issues and Reliability	
- T1 ChatGPT's Cost and Access	

<img src="Image/topic_list.png" style="width:800px;height:220px">

<img src="Image/wordcloud.png" style="width:800px;height:400px">

<hr>


### SENTIMENT-ANALYSIS

- **Comparison of VADER and roBERTa**
  - When comparing VADER and roBERTa, it was found that VADER struggled to identify many positive or negative words in tweerts, often resulting in a polarity score of 0. roBERTa was better at capturing the deeper meaning of a text, allowing it to distinguish between negative and neutral tweets with greater sensitivity.
  - Based on the prediction results, VADER identified positive and neutral tweets as more common, while negative tweets were relatively infrequent (only 12.4%). However, roBERTa's results showed that the number of negative tweets almost doubled (24.1%).
  - In terms of computational efficiency, VADER was significantly faster than roBERTa, taking only 0.49 seconds to analyze 5000 tweets, while roBERTa took 243.42 seconds on a personal desktop.

Overall, VADER is a faster option, but may not capture the nuances of natural language as well as roBERTa. The choice between VADER and roBERTa will depend on the specific task requirements and available computational resources.

<img src="Image/polarity.png" style="width:450px;height:300px"> 

<img src="Image/sentiment1.png" style="width:750px;height:300px"> 

- **Sentiment Over Time (based on roBERTa results)**
<img src="Image/sentiment_time.png" style="width:750px;height:300px"> 

- **Sentiment of Each Topics**
  - Topic T8 **Impacts on Work and Efficiency** and T7 **Impacts on Future Business and Industry** received the most positive sentiment of approximate 50%, indicating people's optimism about the postive effects of ChatGPT on furture work and life.
  - Topic T5 **ChatGPT's Issues and Reliability** and T9 **Impacts on Education and Academy** received relatively more negative sentiment, approximately 46% and 30%, resperctively. This indicates that there is room for improvement in terms of user experience, system stability, watermarking for preventing plagiarism, etc.

  Overall, early users of ChatGPT expressed mainly positive or neutral sentiments regarding its performance in assisting human tasks in various domains, such as business analysis, software development, and NLP. However, a limited percentage of users expressed concerns about potential misuse of ChatGPT and its reliability. 
<img src="Image/sentiment_topic.png" style="width:750px;height:300px"> 

<hr>

## CONCLUSION

This study focused on showcasing the discussions about ChatGPT on Twitter, utilizing a dataset comprising 1.25 million tweets by leveraging machine learning and text analytics. Exploratory data analysis was conducted first on the collected dataset to understand the characteristics of early ChatGPT users. Further, topic modeling was performed to identify the main topics, followed by quantitative sentiment analysis on each topic. The study provides valuable insights into the sentiments of early ChatGPT users and emphasizes the importance of continued research and conversation to develop best practises for the responsible use of large language models. 

<hr>

## REFERENCES
- Chandrasekaran, Ranganathan, et al. "Examining public sentiments and attitudes toward COVID-19 vaccination: infoveillance study using Twitter posts." JMIR infodemiology 2.1 (2022): e33909.
- Haque, Mubin Ul, et al. "" I think this is the most disruptive technology": Exploring Sentiments of ChatGPT Early Adopters using Twitter Data." arXiv preprint arXiv:2212.05856 (2022).
- Scraping Tweets with snscrape: https://github.com/rashidesai24/Analyzing-Twitter-Trends-On-COVID-19-Vaccinations#-data-coverage-
- Topic Modeling: https://medium.com/@kurtsenol21/topic-modeling-lda-mallet-implementation-in-python-part-1-c493a5297ad2
- Sentiment Analysis: https://medium.com/@amanabdulla296/sentiment-analysis-with-vader-and-twitter-roberta-2ede7fb78909

<hr>

