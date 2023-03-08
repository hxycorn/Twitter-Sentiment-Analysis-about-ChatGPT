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


### DATA-PREPROCESSING

### DATA-MODELING

## DATA-VISUALIZATION

## RESULTS 

## CONCLUSION

## REFERENCES
