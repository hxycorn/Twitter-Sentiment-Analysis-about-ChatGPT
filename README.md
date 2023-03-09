# Twitter-Sentiment-Analysis-about-ChatGPT
A quantitative study on over 1.25 million tweets about ChatGPT, employed data scrapping, data cleaning, EDA, topic modeling, and sentiment analysis.
<hr>

## TABLE OF CONTENT
- [Background](#background)
- [Objective](#objective)
- [Methodology](#methodology)
  - [Tools](#tools)
  - [Data Collection](#data-collection)
  - [Data Preprocessing](#data-preprocessing)
  - [Data Modeling](#data-modeling)
- [Data Visualization](#data-visualization)
- [Results](#results)
- [Conclusion](#conclusion)
- [References](#references)

<hr>

## BACKGROUND
ChatGPT is an artificial intelligence chatbot developed by OpenAI and launched in November 2022. It is built on top of OpenAI's GPT-3 family of large language models and has been fine-tuned (an approach to transfer learning) using both supervised and reinforcement learning techniques. Given the advantages of ChatGPT over traditional chatbots, ChatGPT has attracted more than 1 million users in 5 days and 100 million users in 2 months after it was launched, leaving behind other popular online platforms such as Netflix, Facebook, and Instagram in terms of adoption rates. Some early adopters of ChatGPT believe that it will eventually obsolete several professions related to content creation. it has been demonstrated that ChatGPT is capable of producing high-quality responses to a variety of challenges, including solving coding challenges and generating accurate responses to exam queries.

<img align="center" src="Image/user1.png" style="width:300px;height:250px"> <img align="center" src="Image/user2.png" style="width:400px;height:250px">

<hr>

## OBJECTIVE
Using a mixed-method approach, analyze tweets from December 2022 to January 2023 that mention ChatGPT and express diverse and unstructures opinions. Identify the main topics and sentiments of the conversations and examine perception of early ChatGPT users.

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
    <td>Google Colab, Jupyter Notebook, Twitter</td>
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

## DATA-VISUALIZATION

## RESULTS 

## CONCLUSION

## REFERENCES
