# Analysis of Search Engine Bias & User Behavior Modeling

This repository contains the code and analysis for the Assignment 1 project for the course 

CGS616: Human Centered Computing at the Indian Institute of Technology, Kanpur.



Course: CGS616: Human Centered Computing 


Instructor: Prof. Pragathi Balasubramani 


Group Members:

Ahmad Raza (220088) 

Ashwin Chaubey (220245) 

Shivam Kumar (221013) 

Table of Contents
Project Overview

## Part A: Search Engine Bias Analysis

Objective

Methodology

Key Findings

## Part B: E-commerce User Behavior & Decision Modeling

Objective

Methodology

Key Findings

Technology Stack

Setup and Usage

Project Overview
This project is divided into two distinct parts:


## Part A: Search Engine Bias Analysis: This part involves scraping and analyzing search results from Google, Bing, and Yahoo for the query "Trump and Israel" to explore the nature and extent of algorithmic bias. The analysis compares result frequency, sentiment (polarity), and subjectivity to identify how different engines present information on a sensitive geopolitical topic.






## Part B: E-commerce User Behavior & Decision Modeling: This part uses an e-commerce dataset to perform exploratory data analysis (EDA) on user behavior. It then applies a mathematical framework, the Drift Diffusion Model (DDM), to simulate and understand the decision-making process of users leading to a purchase.



Part A: Search Engine Bias Analysis
Objective <a name="objective-a"></a>
To explore the nature and extent of biases in search results by conducting searches on Google, Bing, and Yahoo for the same query and comparing the results.

Methodology <a name="methodology-a"></a>

Data Collection: A Python script using Selenium in headless mode was developed to automate searches on Google, Bing, and Yahoo for the query "Trump and Israel".






HTML Parsing: BeautifulSoup was used to parse the captured HTML and extract search result titles and links based on engine-specific tags.



Data Analysis: The extracted titles were analyzed using:


Word Clouds: To visualize the most frequent terms for each search engine.


Sentiment Analysis: To determine the polarity (positive, negative, neutral tone) of the search result titles.



Subjectivity Analysis: To measure the degree of objective vs. opinion-based content.


Clustering: To group results and identify the thematic diversity of each search engine.

Key Findings <a name="key-findings-a"></a>
The analysis revealed distinct biases for each search engine:


Google: Exhibits a "diversity bias". It returns a wide array of content, including political analysis, social media trends (e.g., "TikTok," "Mr Beast"), and policy news. The results are largely neutral in tone (low polarity) but are highly subjective, indicating a reliance on opinionated content.






Bing: Demonstrates a "centralizing bias". It focuses on a narrower range of policy-centric and analytical content, prioritizing mainstream political discourse.





Yahoo: Shows a "simplification bias". It emphasizes traditional journalism from international sources (e.g., "BBC," "Al Jazeera") but categorizes them into fewer, less-nuanced groups.





Part B: E-commerce User Behavior & Decision Modeling
Objective <a name="objective-b"></a>
To analyze user behavior on an e-commerce platform to understand the key drivers of revenue and to model the cognitive process of purchase decisions using the Drift Diffusion Model (DDM).


Methodology <a name="methodology-b"></a>

Exploratory Data Analysis (EDA): Analyzed user session data to identify trends related to seasonality, visitor types, page interactions, and revenue generation.


Feature Selection: Used a correlation matrix and a Random Forest classifier to identify the most predictive features for revenue. 


PageValues was identified as the most important feature.


Decision Modeling:

A 

Logistic Regression model was trained to predict the probability of a purchase (p) based on key features.



The purchase probabilities were used to calculate a 

drift rate (v) for each user session, representing the speed and direction of evidence accumulation towards a decision. The formula used was:



v= 
2a
σ 
2
 
​
 ln( 
1−p
p
​
 )



where 

sigma is the noise parameter and a is the decision threshold.

The 

Drift Diffusion Model (DDM) was simulated to model the decision-making process as a stochastic race to a decision boundary (purchase or no purchase):


dx=v⋅dt+σ⋅dW


Key Findings <a name="key-findings-b"></a>

Engagement Drives Revenue: Extended engagement with product pages correlates with purchases.


Page Value is Critical: The PageValues feature, representing the average value of pages visited before a transaction, has the strongest correlation with revenue and the highest feature importance.



Decision Dynamics: The DDM analysis revealed that users with higher engagement had stronger drift rates but took slightly longer to make their final decision.

Technology Stack

Language: Python 


Libraries:


Web Scraping: Selenium, BeautifulSoup 


Data Manipulation: Pandas 


Machine Learning: Scikit-learn (implied by use of Logistic Regression and StandardScaler) 



Data Visualization: Matplotlib, Seaborn, WordCloud (implied by the plots in the report) 




Setup and Usage
Clone the repository:

Bash

git clone https://github.com/your-username/your-repository-name.git
cd your-repository-name
Set up a virtual environment (recommended):

Bash

python -m venv venv
source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
Install the required dependencies:

Bash

pip install pandas selenium beautifulsoup4 scikit-learn matplotlib seaborn wordcloud
Download WebDriver:

For Part A, you need a WebDriver for Selenium to control a browser. Download the appropriate driver for your browser (e.g., ChromeDriver) and ensure it is in your system's PATH or in the project directory.

Run the scripts:

Navigate to the respective directories for each part and run the main Python scripts.
